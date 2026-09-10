# How to Correctly Evaluate AI Models

## Overview

Artificial Analysis composite scores amalgamate nine sub-benchmarks and do not tell the full story of a model's capabilities. The same benchmark can produce incongruent results depending on whether it is run by the official maintainer or an adapted source, due to differences in test repetitions, time budgets, sandbox environments, and harness configuration. To properly evaluate a model, you must examine individual sub-benchmark scores, understand the harness layer being used, and weigh token efficiency and cost efficiency alongside raw intelligence scores.

## When to Follow These AI Teachings

- When comparing new AI model releases and deciding which model to adopt
- When interpreting composite benchmark leaderboards such as Artificial Analysis
- When evaluating whether a model's headline score translates to real-world usefulness
- When choosing between models based on cost efficiency, token usage, and subscription plans
- When assessing claims made in vendor benchmark announcements or blog posts

## Steps

### Step 1: Decompose the Composite Score

Identify the individual sub-benchmarks that make up any composite score. A model ranking first overall does not necessarily rank first on every component. Pull the official source data (such as a system card or official benchmark page) to see exactly where the model places on each sub-benchmark before accepting a headline composite ranking as authoritative.

### Step 2: Identify the Harness Being Used

Determine whether a benchmark measures the bare model or the model operating inside a specific harness. SWE-bench evaluates the model directly by generating code and running tests without an external coding agent layer. Terminal Bench embeds the model inside a harness (such as Terminus 2) and measures the combined model-plus-harness system. The DeepSeek benchmark also embeds the model inside a harness such as Mini Swe Agent. Knowing which harness is pinned is essential because swapping the harness changes the variable being measured.

### Step 3: Verify Benchmark Source and Conditions

Even when two sources claim to report the same benchmark score for the same model and harness, the numbers diverge. Check how many times tests are repeated (official benchmarks require five repetitions; adapted sources run three repetitions), the time budget per task, and sandbox configuration. These conditions affect reproducibility and must be matched or normalized before comparing scores across sources.

### Step 4: Evaluate Token Efficiency

Look at the number of output tokens generated per task alongside the score. Fable 5, scoring 70 percent while generating 119,000 output tokens, is far less efficient than a model that scores 73 percent while generating 60,000 tokens. Token efficiency directly impacts cost and throughput in production and should be weighed alongside raw accuracy.

### Step 5: Evaluate Cost Efficiency

Calculate or compare the cost per task across candidate models. Two models can achieve similar scores while differing dramatically in cost per task. Models from OpenAI (GPT 5.6 Soul), xAI (Grok 4.6), DeepSeek (V4 Pro), and Google (Gemini 3.8 Flash) are cited as examples of cost-efficient alternatives that can outperform or match more expensive models at two to four times less cost.

### Step 6: Factor in Subscription and Access Constraints

Before adopting a top-ranked model, verify its availability under your current subscription tier. Providers gate their most capable models behind higher-tier plans or limit weekly token allowances even on expensive max plans. A model's practical usability depends on whether you can actually access and afford to run it at scale.

## Examples

### Example 1: Fable 5.1 on Artificial Analysis vs DeepSeek

Fable 5.1 held the top composite score on Artificial Analysis, but examination of individual sub-benchmarks revealed it scored second on SWE-bench, sixth on Terminal Bench, and seventh on the DeepSeek benchmark. Fable 5.1 scored 67.4 percent on the DeepSeek benchmark, placing the model closer to GPT 5.6 Soul, Luna, and Grok 4.6 than to the top tier. Relying solely on the composite ranking would have overstated its dominance.

### Example 2: Terminal Bench Official vs Artificial Analysis Adaptation

The official Terminal Bench benchmark reported Fable 5 operating within the Terminus 2 harness at 80.5 percent, while Artificial Analysis reported the same model and harness at 84 percent. Both sources refer to the same benchmark, same model, and same harness, yet the numbers differ because of differences in test repetitions, time budget, and sandbox configuration. Treating either number as the universal score without understanding these conditions leads to incorrect conclusions.

### Example 3: Token Efficiency Comparison

Fable 5 generated 119,000 output tokens while scoring 70 percent on the DeepSeek benchmark. GPT 5.6 Soul scored higher at 73 percent while using only 60,000 output tokens. Gemini 3.8 Flash also demonstrated lower cost per task as it approached top scores. Anthropic models were found to be less token-efficient than competing models, and this inefficiency is reflected in higher subscription costs and faster token allowance consumption.

### Example 4: Subscription Plan Practicality

Fable 5.1 is not included in Anthropic's standard Pro membership at $20 per month, requiring either additional usage credits or an upgrade. Even the $200 max plan does not deliver 20 times the weekly allowance of the Pro plan because the multiplier applies only to a rotating 5-hour window, making the effective increase six times rather than 20 times. This gap between marketing language and actual deliverable allowance is a practical constraint that affects whether the model is viable for production use.

## Best Practices

- ✅ Decompose composite benchmark scores into individual sub-benchmark results before drawing conclusions
- ✅ Identify and document the exact harness, test repetition count, time budget, and sandbox used for any benchmark result
- ✅ Compare token efficiency (output tokens per task) alongside raw accuracy scores
- ✅ Calculate or compare cost per task across candidate models before selecting a model for production
- ✅ Verify model availability and actual token allowances under your current subscription tier before committing
- ✅ Check the official benchmark source directly rather than relying on vendor summaries or blog announcements

## Keep In Mind

- The video teaches that the definition of a "good" model has shifted from pure intelligence to a combination of intelligence, token efficiency, cost efficiency, and practical usability in coding environments and agents such as Cursor, Claude Code, and OpenAI Codex.
- The AI model landscape evolves continuously; a model that leads today is matched or surpassed by cheaper, more efficient alternatives.
- Vendor benchmark announcements and blog posts selectively highlight favorable conditions and omit unfavorable ones; always cross-reference with official system cards and benchmark pages.

## Security & Safety Notes

- When using AI coding agents on untrusted networks, ensure your internet traffic is secured through a VPN with a no-logs policy and independent security audits to protect your browsing patterns, IP address, and location data.
- Be aware that coding agents running on terminals, mobile apps, and cloud platforms transmit data over networks; treat these as potential vectors for exposure of proprietary code and sensitive project information.

## Common Pitfalls

- **Problem:** Assuming that a model ranked first on a composite leaderboard is best at every individual task.
  **Solution:** Always inspect the individual sub-benchmark breakdown to understand where the model actually ranks across different task types.
- **Problem:** Treating benchmark scores from different sources as directly comparable when the harness, repetitions, or time budget differs.
  **Solution:** Verify the experimental conditions for every score before comparing; normalize or discard scores that do not share the same conditions.
- **Problem:** Prioritizing raw intelligence scores while ignoring token efficiency and cost per task.
  **Solution:** Factor token output and cost per task into every model evaluation, as these directly determine production feasibility and ongoing cost.
- **Problem:** Misinterpreting subscription marketing language as literal multipliers of actual usable allowance.
  **Solution:** Read the plan's published token allowance terms; "20x" or "max" labels refer to short-term token bursts and flexible weekly allowance pools rather than proportional increases in total weekly or monthly tokens.
- **Problem:** Adopting a top-ranked model without verifying it is accessible under your current plan.
  **Solution:** Confirm model availability and effective token limits under your subscription before committing to integration or migration.
