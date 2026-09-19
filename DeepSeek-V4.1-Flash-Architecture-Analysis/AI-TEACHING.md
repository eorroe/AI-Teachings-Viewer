# DeepSeek V4.1 Flash Architecture Analysis: Engram, Causal Encoder-Decoder (CED), Cross-Layer Sparse Attention 2 (CSA 2), and Single-Pass MHC (Mixture of Hierarchical Channels)

## Overview

This AI Teaching document provides a structured analysis of DeepSeek V4.1 Flash's architectural innovations, including the Engram module for recurring local pattern storage, Causal Encoder-Decoder (CED) architecture for compute efficiency, Cross-Layer Sparse Attention 2 (CSA 2) for KV cache optimization, and Single-Pass MHC for kernel-level memory optimization. This document explains how these components combine to achieve a 437x reduction in key-value (KV) cache footprint (from 389 KB per token for a standard 40-layer Transformer with hidden dimension 5,120 to 890 bytes per token overall for the optimized model combining all four components, as attributed to the DeepSeek V4.1 Flash Architecture Analysis video transcript) and reduces prefill compute by 50% relative to the full 40-layer model. The architecture preserves layer-specific learned KV projections and attention head diversity. The teaching synthesizes the four architectural components into structured implementation steps for analyzing or implementing architectural decisions in DeepSeek V4.1 Flash.

## When to Follow These AI Teachings

- When you need to analyze or compare DeepSeek V4.1 Flash with KV cache compression
- When working on reducing prefill floating-point operations (FLOPs) for models with long context windows (1M tokens)
- When implementing or studying the Engram module for recurring local pattern memorization
- When analyzing DeepSeek V4.1 Flash architecture, Engram modules, CED architecture, CSA 2, or Single-Pass MHC

## Steps

### Step 1: Understand the Engram Module Architecture

The Engram module is a separate learnable storage system that delegates the storage of recurring local patterns (2-gram, 3-gram, and 4-gram token sequences) from the core transformer layers. It operates by taking the current token and looking back 2, 3, and 4 tokens to form n-grams and use the resulting n-grams as IDs, mapping each n-gram ID to a 256-dimensional vector in the hash table. This allows the model to look up previously encountered 2-gram, 3-gram, and 4-gram token sequences at inference time rather than recomputing them through attention.

To implement an Engram-like system:
1. Define n-gram extractors for 2-gram, 3-gram, and 4-gram patterns (n=2, 3, 4).
2. Reduce the vocabulary size for the Engram from the full token vocabulary of 129,280 to a subset of 99,000 by consolidating similar tokens into a smaller subset mapped to the same hash bucket.
3. Assign eight hash heads to each Engram, with a total of 384M rows per Engram instance as the maximum capacity.
4. If operating at maximum capacity, calculate total storage as: total_rows × embedding_dimension. For 384M rows × 256 dimensions = 98.3 billion parameters per Engram instance, totaling 196 billion parameters for two Engram instances.
5. Inject the Engram output into specific layers of the backbone (layers 1 and 15) rather than every layer to control where cached patterns influence computation.

### Step 2: Implement Causal Encoder-Decoder (CED) for Compute Efficiency

CED divides the DeepSeek V4.1 Flash model into encoder and decoder halves to reduce prefill compute by 50% relative to the full 40-layer model while maintaining full decode capability. During prefill, only layers 1 through L/2 process input tokens and build a shared hidden representation. During decode, all layers run for each token, using the shared hidden state as a shared reference.

To implement CED:
1. Divide the total layer count (L) in half. For a 40-layer model, the split occurs at layer 20.
2. During prefill, run only layers 1 through L/2 to build the shared global KV cache and hidden state.
3. During decode, run all L layers, where layers L/2+1 through L reference the shared hidden state from layer L/2.
4. Allow subsequent layers to maintain their own layer-specific KV states with learned projections, rather than forcing all layers to share an identical global cache.
5. Mathematically, the hidden state for layer l > L/2 combines the shared hidden state H_{L/2} with the layer's own learned KV projection, where W_proj is the learned projection matrix: H_l = H_{L/2} × W_proj + KV_l.

### Step 3: Apply CSA 2 Modes for KV Cache Reuse

CSA 2 (Cross-Layer Sparse Attention 2) introduces three modes to selectively reuse or index KV cache across layers by allowing layers to reuse or index a shared global KV state rather than independently building a full KV state:

- **Full Mode**: The layer builds its own fresh KV states, indexes them to produce the top 48 entries, and adds them to core attention.
- **Index Mode**: The layer reuses the previous global KV from the most recent layer operating in full mode, generates a new query for the current layer, runs the indexer again to choose new top 48 entries, and adds them to core attention.
- **Reuse Mode**: The layer keeps both the global KV and the same top 48 selection from the most recent layer operating in full mode, computing its own attention over those previously selected KV entries without rebuilding or reindexing.

To apply CSA 2:
1. Assign full mode to layers 1–20 and index or reuse mode to layers 21–40.
2. For layers in full mode, build fresh KV states, run the indexer to select the top 48 entries, and add to core attention.
3. For layers in index mode, reference the most recent layer operating in full mode's global KV, generate a new query, and re-run the indexer for the top 48 selection.
4. For layers in reuse mode, directly attend to the most recent layer operating in full mode's already-selected KV entries without any reindexing.
5. Use the hierarchical sparse indexer to limit the search space: group positions into blocks of 8, find the highest attention score relative to the current layer's query in each block, and keep the top 48 blocks as candidates for reindex.

### Step 4: Configure Hierarchical Sparse Indexer for Candidate Selection

The hierarchical sparse indexer reduces the search space from 16,384 positions to 384 positions for KV cache reindexing by organizing positions into blocks and selecting only the candidates with the highest attention scores relative to the current layer's query in each block.

To configure the indexer:
1. Group sequence positions into blocks of 8 tokens each.
2. Within each block, identify the position with the highest attention score relative to the current layer's query.
3. Select the top 48 blocks based on their highest attention scores relative to the current layer's query.
4. The total candidate pool becomes 48 blocks × 8 positions = 384 positions. The total search space for reindex operations is 16,384 positions.
5. Use this reduced candidate set for reindex operations instead of scanning the entire global context, reducing the search space from 16,384 to 384 positions.

### Step 5: Optimize Kernels with Single-Pass MHC

Single-Pass MHC (Mixture of Hierarchical Channels) reduces HBM read/write traffic in the residual network's data movement between high-bandwidth memory (HBM) and registers by modifying the residual connection formula to eliminate the read-after-write hazard on coefficient A, reducing memory read/write operations from 20d to 10d (where d is the hidden dimension).

To optimize with Single-Pass MHC:
1. Note that the original MHC splits residual connections into four channels, where each channel learns a gating scalar via a learned projection to determine how much information passes through, but requires three separate kernel operations: computing coefficients, applying the input transformation, and computing the final output.
2. Recognize that the original implementation requires 20d operations per residual connection for n=4 channels, where d is the hidden dimension and n is the number of channels, which is above the lower bound of 10d operations, since the inefficiency is formally expressed as 4d(n+1) operations (20d with n=4 channels) and the lower bound as 2d(n+1) operations (10d with n=4 channels).
3. Restructure the algebra by shifting the temporal dependency: move the A coefficient computation (the learned gating scalar for the first channel) earlier in the computation sequence since A depends only on the input and not on subsequent computations in that sequence, enabling a single kernel pass.
4. Fuse the three kernel operations into a single kernel pass by changing the order of operations, not by fusing existing kernels (distinct from Mega MHC, a post-hoc kernel-fusion approach that combines separately compiled kernels into a single fused kernel launch after individual kernels have been defined).
5. Achieve the lower bound of 2d(n+1) operations by restructuring the algebra to remove the three separate kernel operations, allowing a single kernel pass to compute all required variables at once, eliminating unnecessary HBM-to-register traffic.

## Examples

### Example 1: Building a Compressed KV Cache System with CSA 2

When designing a model for 1 million token context windows, apply CED to reduce prefill compute by 50%, then use CSA 2 full mode for the first half of layers and index or reuse mode for the second half. For example, in a 40-layer model, build the global KV cache during prefill using only the first 20 layers, then during decode, let layers 21-30 attend to the shared cache with reindexing in index mode and layers 31-40 in reuse mode. This combination of all four architectural components reduces the overall KV cache to 890 bytes per token for the optimized model, so a 1M-token context window requires 890 MB. By comparison, a standard 40-layer Transformer with standard multi-head attention and the same hidden dimension of 5,120 requires 389 GB of KV cache for a 1M-token context window.

### Example 2: Implementing a Local Pattern Cache with Engram

For a model that encounters 3-gram and 4-gram token patterns that match keys in the Engram hash table, implement an Engram module that stores 256-dimensional vectors keyed by 3-gram and 4-gram token patterns. During model inference, when a 3-gram or 4-gram token pattern matches a key in the Engram hash table, the model retrieves the cached representation from the Engram table instead of processing it through the attention mechanism. The 256-dimensional vector retrieved from the Engram table is a learned parameter stored there during model training and directly usable during model inference.

### Example 3: Reducing Kernel Inefficiency in Residual Networks

When deploying a model with MHC on graphics processing units (GPUs), apply Single-Pass MHC to reduce memory read/write operations from 20d to 10d. For a 40-layer model with 4 channels per residual connection, the baseline MHC implementation requires 20d operations per residual, where d is the hidden dimension. By restructuring the algebra to shift the A coefficient (the learned gating scalar for the first channel) earlier in the computation sequence, all required intermediate values (the A, B, and C coefficients and the input transformation X̂, the current input X transformed by the A coefficient) become available simultaneously, allowing a single kernel to compute the output at the lower bound, reducing memory read/write operations from 20d to 10d.

## Best Practices

- ✅ Separate memorization of recurring local patterns (2-gram, 3-gram, and 4-gram token sequences) into dedicated modules including Engram to reduce the KV state storage per layer
- ✅ Use CED architecture for inference workloads where prompt processing accounts for most of the total inference FLOPs
- ✅ Apply CSA 2 modes selectively based on layer depth, using full mode for layers 1–20, index mode for layers 21–30, and reuse mode for layers 31–40
- ✅ Use hierarchical sparse indexing to limit candidate positions to 384, drawn from a 16,384-position search space within the 1M-token sequence, instead of scanning the entire 1M-token sequence
- ✅ Restructure the residual connection algebra to shift the temporal dependency order and eliminate read-after-write hazards for Single-Pass MHC before attempting kernel fusion
- ✅ Consolidate token vocabularies for external memory modules to reduce the 129,280-token key space to a 99,000-token subset
- ✅ Verify KV cache footprint reductions against the baseline of 389 KB per token for a standard 40-layer Transformer

## Keep In Mind

- Engram parameters are learned during model training and are directly usable during model inference; they total 196,608,000,000 Engram-specific parameters (assuming maximum capacity of 384M rows × 256 dimensions × 2 instances)
- CED splits compute between prefill and decode (based on the 40-layer DeepSeek V4.1 Flash architecture); the prefill savings are due to running only layers 1–20 during prompt processing
- CSA 2 does not force every layer to independently build KV; it introduces modes to reuse or reindex previous global KV states
- Single-Pass MHC is distinct from Mega MHC; it changes algebra to remove temporal dependencies rather than fusing existing kernels
- The DeepSeek V4.1 Flash architecture defines learned projection pathways (W_proj) for information flow, where the optimizer updates W_proj via backpropagation during training to minimize the loss function, implementing the transformation H_l = H_{L/2} × W_proj + KV_l as defined in Step 2

## Security & Safety Notes

- Engram modules store learned representations of token sequence patterns (such as 2-gram, 3-gram, and 4-gram token sequences)
- Verify Single-Pass MHC implementation by running performance benchmarks to verify that operation count remains at the lower bound of 2d(n+1) — which equals 10d for n=4 channels — after implementing the algebraic restructuring.

## Common Pitfalls

- **Problem:** Assuming the Engram module exclusively stores recurring 2-gram, 3-gram, and 4-gram token patterns
  **Solution:** Note that the main backbone also learns these 2-gram, 3-gram, and 4-gram token patterns; the Engram module's separate hash table pathway is a designed architectural inductive bias that gives the model a dedicated route to store and retrieve short token sequences, with gradient descent determining how much the backbone versus the Engram pathway actually learns those patterns, offering a separate pathway rather than exclusive storage
- **Problem:** Applying CED by sharing a single global KV cache across all layers without layer-specific projections reduces footprint but prevents each layer from maintaining its own learned KV projections, preventing distinct per-layer attention-head specialization patterns
  **Solution:** Allow layers after the split to maintain their own learned KV projections in addition to referencing the shared hidden state, preserving distinct per-layer attention-head specialization patterns
- **Problem:** Using CSA 2 reuse mode for all 40 layers, losing the ability to incorporate new tokens into layer-specific KV states
  **Solution:** Use full mode for layers 1–20, index mode for layers 21–30, and reuse mode for layers 31–40 to preserve KV cache efficiency without sacrificing the ability to incorporate new tokens into layer-specific KV states
- **Problem:** Confusing Single-Pass MHC with kernel fusion
  **Solution:** Single-Pass MHC restructures algebra to eliminate the read-after-write hazard on coefficient A; kernel fusion is a separate optimization applied afterward
- **Problem:** Miscalculating Engram storage requirements due to the full token vocabulary of 129,280
  **Solution:** Consolidate the token vocabulary and use hash heads with limited rows (384M total rows per Engram instance) to bound memory usage
