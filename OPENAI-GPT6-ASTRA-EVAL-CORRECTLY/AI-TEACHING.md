# How to Correctly Evaluate AI Models Using Benchmarks

## Overview

This AI Teaching is a structured guide for interpreting and evaluating AI model benchmark results, using GPT-6 Astra as a case study. It addresses how composite benchmarks can mislead when their sub-benchmark coverage does not match your evaluation goals, the importance of understanding evaluation harnesses, and how to distinguish between token efficiency and cost efficiency when comparing frontier models from leading labs. Model names, benchmark scores, and pricing shown below are drawn from the source material and may reflect hypothetical or illustrative examples rather than released products.

## When to Follow These AI Teachings

- When you need to evaluate AI model performance beyond aggregate benchmark rankings
- When working with composite benchmarks that aggregate multiple sub-benchmarks
- When comparing models using benchmarks like ARC AGI-3, Frontier Math, or the DeepSeek benchmark
- When the user asks whether a model's benchmark score reflects performance on practical coding and reasoning tasks

## Steps

### Step 1: Understand the Composite Benchmark Wrapper Problem

The Composite Benchmark Wrapper Problem occurs when a single composite score hides the fact that the included sub-benchmarks do not match your evaluation priorities. Composite benchmarks aggregate multiple individual benchmark scores into one number. This aggregation is useful when the included benchmarks match your use case; the composite score becomes misleading when capabilities that matter for your specific use case are omitted or weighted incorrectly. When OpenAI announced GPT-6 Astra with 14 benchmarks, only 1 of those 14 overlapped with the Artificial Analysis Intelligence Index benchmarks, placing GPT-6 Astra in fifth place in the Artificial Analysis Intelligence Index composite ranking. The Artificial Analysis Intelligence Index is a composite ranking that aggregates multiple sub-benchmarks. This gap shows that the composite index omitted most of OpenAI's highlighted benchmarks. Always inspect the underlying individual benchmarks rather than relying solely on a composite score.

### Step 2: Evaluate ARC AGI-3 Results with Harness and Dataset Awareness

When assessing ARC AGI-3 scores, consider both the harness used and the dataset privacy tier. Dataset privacy tier indicates who may access or inspect the evaluation data (for example, public, semi-private, or fully private). The Arc Foundation provides evaluation prompts representing a 64x64 grid with 16 colors as JSON objects. Opus 5, using the Evo harness, scored 100% on the ARC AGI-3 public dataset. Evo is an agentic harness that provides persistent memory, context management, and an execution environment. GPT-6 Astra scored 99.9% on the ARC AGI-3 semi-private dataset when evaluated with OpenAI's own harness, but scored only 62.7% on the ARC AGI-3 semi-private dataset when evaluated using the Arc Foundation's harness. The Arc Foundation created ARC AGI-3 and administers the semi-private dataset, yet the potential for data leak exists since GPT-6 Astra makes API calls during evaluation. Always verify which harness, dataset split, and evaluation conditions produced a given score before drawing conclusions.

### Step 3: Evaluate Frontier Math Results with Independent Proctoring

Frontier Math is created and independently administered by Epoch AI, an independent AI research organization. Problems range from Tier 1 (linear algebra, group theory) to Tier 4 (the benchmark's hardest category). GPT-6 Astra scored 97.6% on Frontier Math Tier 4, while Thebault 5.1 scored 87.8% on Frontier Math Tier 4. Because Epoch AI controls both the Frontier Math data and the evaluation process independently of any model lab, Frontier Math provides a more trustworthy signal of mathematical reasoning capability.

### Step 4: Analyze Token Efficiency Against Cost Efficiency

Token efficiency and cost efficiency are distinct metrics. Token efficiency measures how many output tokens a model uses to accomplish a given task, while cost efficiency measures the price per million tokens. GPT-6 Astra is token-efficient: it used fewer output tokens than GPT-5.6 Soul on the DeepSeek benchmark. Fewer output tokens for equivalent benchmark performance indicates higher token efficiency. However, GPT-6 Astra is not cost-efficient: it is priced at $10 per million input tokens and $50 per million output tokens for short-context requests, versus GPT-5.6 Soul at $4 per million input tokens and $20 per million output tokens for short-context requests. When evaluating models, compare token usage columns on benchmarks like DeepSeek, but separately verify pricing to determine actual cost efficiency for your use case.

### Step 5: Redefine What Constitutes a Good Model

The definition of a good model is shifting from pure intelligence measured by benchmark scores toward a multidimensional view that includes token efficiency, cost efficiency, speed, and real use case performance. A model that scores in the top tier on OpenAI's 14 highlighted benchmarks but is expensive and uses more tokens than alternatives may be less useful than a model with a marginally lower composite benchmark score that has lower inference latency and lower cost. Use cases where models must solve open-ended realistic tasks (such as the DeepSeek benchmark and Exploit Bench, which test coding and security-related tasks) are more predictive of real-world outcomes for software engineers and AI practitioners than highly abstracted benchmarks like ARC AGI-3.

## Examples

### Example 1: ARC AGI-3 Harness Comparison

GPT-6 Astra scored 99.9% on ARC AGI-3 when OpenAI evaluated it. The same model scored 62.7% when the Arc Foundation evaluated it using their official ARC AGI-3 harness. Opus 5 scored 100% on the ARC AGI-3 public dataset when evaluated using the Evo harness. Before concluding that GPT-6 Astra has higher ARC AGI-3 performance than other models, verify the harness and dataset tier, because the evaluation conditions directly affect comparability.

### Example 2: Frontier Math Tier 4 Performance

GPT-6 Astra scored 97.6% on Frontier Math Tier 4, while Thebault 5.1 scored 87.8%. Because Epoch AI independently proctors Frontier Math and keeps all data private, these scores are comparable across model labs and reflect genuine differences in advanced mathematical reasoning.

## Best Practices

- ✅ Inspect the underlying individual benchmarks rather than relying solely on composite scores
- ✅ Verify which harness, dataset tier, and evaluation conditions produced a given benchmark score
- ✅ Compare token efficiency by examining output token columns on benchmarks like DeepSeek
- ✅ Verify pricing per million tokens separately from benchmark performance to assess cost efficiency
- ✅ Prioritize benchmarks that reflect realistic use cases and practitioner workflows
- ✅ Consider independent proctoring when evaluating benchmark credibility

## Keep In Mind

- The Artificial Analysis Intelligence Index placed GPT-6 Astra in fifth place, highlighting that composite rankings can diverge significantly from individual benchmark performance
- GPT-6 Astra scored 100% on Exploit Bench, 99.9% on ARC AGI-3, and 97.6% on Frontier Math Tier 4
- GPT-6 Astra scored 74% on the DeepSeek benchmark while GPT-5.5 scored 7 to 8 percentage points lower
- Gemini 3.8 Flash and Anthropic's Opus 5 achieve similar scores to Astra on the DeepSeek benchmark but use more output tokens per task
- The AI industry is experiencing a shift toward token efficiency, where equivalent benchmark performance is achieved with fewer tokens

## Security & Safety Notes

- Semi-private and fully private benchmark datasets are hidden from the public, but data leak risk remains if models make API calls during evaluation
- Always verify whether benchmark evaluation environments are hosted by the benchmark creator or by the model lab, as this affects data privacy guarantees

## Common Pitfalls

- **Problem:** Assuming a composite benchmark score accurately represents model intelligence
  **Solution:** Examine the individual benchmarks underneath the composite and verify overlap with your relevant evaluation criteria
- **Problem:** Comparing benchmark scores across different harnesses or dataset tiers
  **Solution:** Only compare scores produced under identical harness, dataset, and evaluation conditions
- **Problem:** Conflating token efficiency with cost efficiency
  **Solution:** Evaluate output token usage and pricing per million tokens as separate dimensions
- **Problem:** Selecting a model based solely on aggregate benchmark scores
  **Solution:** Weight token efficiency, cost efficiency, speed, and real use case performance alongside raw benchmark scores
