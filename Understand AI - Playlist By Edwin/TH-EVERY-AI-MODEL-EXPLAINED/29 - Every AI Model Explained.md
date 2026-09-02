# Every AI Model Explained

## Overview

This AI teaching explains how to categorize AI models by capability, size, speed, and cost, and how to select the right model for each task. It breaks models into five categories — flagship, light, mid-tier, open source, and specialist — and demonstrates practical selection criteria using real examples. The goal is to stop being overwhelmed by new model releases by understanding the underlying categories that remain stable over time.

## When to Follow These AI Teachings

- When you need to choose an AI model for a specific project, task, or workflow
- When you want to understand why one model is faster or cheaper than another
- When you are processing sensitive data (financial documents, emails, private records) and need to decide between hosted and open source options
- When you need to run time-sensitive tasks and must prioritize speed over depth
- When comparing at least three model outputs for the same prompt using a model council
- When you want to avoid paying for individual model subscriptions by using a single aggregator platform

## Steps

### Step 1: Understand the Model Spectrum

AI models can be categorized into five groups based on capability, size, speed, and cost:

- **Flagship** models: Large, capable, expensive, slower. Examples: GPT-5.2, Claude Opus 4.6, Grok 4.1, Gemini 3 Pro. Use for complex multi-step tasks, multimodal work, and tasks requiring the highest capability.
- **Light** models: Fast, low cost, limited capacity relative to flagship. Examples: Gemini 3 Flash, which retains 90–95% of Gemini 3 Pro capability through knowledge distillation but runs faster. Use for time-pressured tasks where speed matters more than depth.
- **Mid-tier** models: Balanced capability, moderate cost, suitable for everyday queries. Examples: Claude Sonnet 4.5, which the speaker recommends as the default for writing, code generation, and building interactive dashboards. These handle 80% of everyday queries.
- **Open source** models: Downloadable and runnable locally at no ongoing per-query cost, unlike hosted models that charge subscriptions or API fees. Examples: Kimi K2.5. Use when you need full data control, privacy, or zero ongoing cost.
- **Specialist** models: Built for domain-specific tasks. Example: Perplexity's Sonar model, built on the open-source Llama 3.3 7B model and fine-tuned for research with retrieval-augmented generation (RAG) and citation infrastructure. Use for research with citations, medical data analysis, or legal review.

### Step 2: Identify Your Task Requirements

Determine what matters most for your use case: raw capability, speed, cost, privacy, or domain specialization. If you need multi-step reasoning, multimodal analysis, or image generation, you need a flagship model. If you need a fast result under time pressure, use a light model. If you need the best writing or code quality regardless of cost, use a flagship like Claude Opus 4.6. If you need data privacy or local execution, use an open source model.

### Step 3: Choose the Right Model Category

- **Flagship** — Use for complex multi-step tasks, multimodal work (image + text analysis), and tasks requiring the highest capability. Examples: GPT-5.2, Claude Opus 4.6, Grok 4.1, Gemini 3 Pro.
- **Light** — Use when speed matters more than depth. Gemini 3 Flash retains 90–95% of Gemini 3 Pro capability through knowledge distillation but runs faster. Use for time-pressured tasks such as report analysis when you have one minute before a meeting, according to the speaker.
- **Mid-tier** — Use for everyday queries — tasks that do not require the maximum capability of a flagship model, including writing, code generation, and building interactive dashboards from scratch. Claude Sonnet 4.5 is the recommended default: writing and code generation skills, less expensive than Opus, good for building apps from scratch and creating dashboards.
- **Open source** — Use when you need full data control, privacy, or zero ongoing cost. Kimi K2.5 is an example. Download it locally to process sensitive financial statements or personal emails without sending data to third-party platforms.
  - **Specialist** — Use for domain-specific tasks like research with citations, medical data analysis, or legal review. Perplexity built its Sonar model on the open-source Llama 3.3 7B model and fine-tuned it for research with retrieval-augmented generation (RAG) and citation infrastructure.

### Step 4: Access Models Efficiently

Use a model aggregator platform like Perplexity AI to access multiple models (including GPT-5.2, Claude Opus 4.6, Grok, Gemini, and Kimi) through a single subscription instead of paying for individual Application Programming Interface (API) access. This avoids the cost of maintaining multiple separate subscriptions. For open source models, you can either download and run them locally or use Perplexity's hosted Kimi K2.5 option, noting that the hosted version runs on Perplexity's US servers.

### Step 5: Apply Model-Specific Best Practices

Enable thinking mode on flagship models like GPT-5.2 and Claude Opus 4.6 to get better reasoning on complex tasks — it will be slower but produces stronger results. Use model council features (available on Perplexity) to run a single prompt across multiple models simultaneously and compare outputs directly. For open source models, apply fine-tuning, RAG systems, and custom tooling to adapt them to specialist tasks.

### Step 6: Categorize New Models as They Appear

When new models are released, place them into the existing categories (flagship, light, mid-tier, open source, specialist) rather than treating each as a completely new decision. Model versions are regularly updated and individual models are replaced by newer versions over time, but the five categories (flagship, light, mid-tier, open source, specialist) remain stable and are the framework for making decisions.

## Examples

### Example 1: Analyze Customer Feedback with a Flagship Model

Use GPT-5.2 through Perplexity with thinking mode enabled. Attach a CSV of 500 rows of customer feedback and prompt: "Analyze this customer feedback CSV. Group the complaints by category. Draft a markdown customer response template for the complaints. Then generate a banner for the upcoming workshop on AI agents in Paris, France." GPT-5.2 handles the multi-step task chain (analysis, templating, and image generation) in one run because of its multimodal capability.

### Example 2: Generate Code with Claude Opus 4.6

Use Claude Opus 4.6 for code generation and refactoring tasks. Example: paste an open-source agent workflow script and ask it to refactor the code so the user can input a desired email address and add a simple dashboard frontend to display categorized emails visually. Claude Opus 4.6 excels at this because its primary specialization is code generation and writing.

### Example 3: Compare Emotional Tone Across Models with Model Council

Use Perplexity's model council feature to compare how three models respond to an emotional prompt. Select GPT-5.2, Claude Opus 4.6, and Grok 4.1. Submit the same prompt (for example, a personal struggle with startup failure and co-founder tension). Compare results: Grok will respond with high emotional empathy and brevity. Claude will respond with action-oriented empathy. GPT-5.2 will provide a more analytical, slightly rambling response. Use this to select the model whose tone matches the use case.

### Example 4: Emergency Report Analysis with Gemini 3 Flash

Download a large report (for example, a global climate highlights report). Prompt: "Create an executive summary and three key insights from this report." Use Gemini 3 Flash when under time pressure (for example, a meeting in one minute). Gemini Flash will return a brief executive summary, while Gemini 3 Pro will take longer but provide deeper analysis with more specific numbers and evidence. Use Flash for speed, Pro for depth.

### Example 5: Build an Interactive Dashboard with Claude Sonnet 4.5

Prompt Claude Sonnet 4.5: "Build an interactive web app that can visualize lunar cycles." Sonnet handles building-from-scratch tasks well without needing the full power of Opus. Use Sonnet for analyses followed by dashboard and visualization creation.

### Example 6: Privacy-Sensitive Financial Analysis with Kimi K2.5 (Open Source)

Download Kimi K2.5 and run it locally to analyze personal financial statements and daily emails. Because the model runs on your machine, no data is sent to third-party platforms. This is the correct choice when privacy matters more than raw capability, and when running the model at least 100 times per day (for example, processing over 100 emails) would be cost-prohibitive on a hosted API.

### Example 7: Research with Citations Using Sonar (Specialist Model)

Use Perplexity's Sonar model to answer researcher-specific questions like: "What are the current FDA approval status, clinical trial results, side effects, and expert opinions on semaglutide liraglutide for weight loss in non-diabetic patients?" Sonar searches multiple sources, filters for credibility, and returns results with inline citations.

### Example 8: Character-Consistent Image Generation with Gemini 3 Pro

Prompt Gemini 3 Pro: "Generate an image of a professional woman named Sarah." Follow up with: "Now generate the same woman in different scenarios: teaching in front of a whiteboard with AI diagrams, working on a laptop in a coffee shop, leading a workshop with students in the background, recording a video tutorial at her desk." Gemini 3 Pro maintains character consistency across multiple generated images of the same person in different scenarios, according to the speaker.

## Best Practices

- ✅ Use a model aggregator like Perplexity AI to access multiple models through a single subscription rather than paying for individual API access
- ✅ Enable thinking mode on flagship models for complex reasoning tasks, accepting the slower speed in exchange for better results
- ✅ Default to a mid-tier model like Claude Sonnet 4.5 for everyday tasks, and only escalate to a flagship when the task genuinely requires it
- ✅ Use open source models when handling sensitive data such as financial records, personal emails, or private documents
- ✅ Use a model council feature to compare outputs across multiple models for the same prompt before committing to one
- ✅ Categorize new models into existing categories (flagship, light, mid-tier, open source, specialist) rather than treating each launch as a new decision
- ✅ Use light models like Gemini 3 Flash for time-pressured tasks where speed matters more than depth
- ❌ Do not send sensitive data (financial records, private emails) through closed-source third-party platforms when an open source alternative exists
- ❌ Do not pay for flagship model subscriptions for tasks that a mid-tier model can handle
- ❌ Do not expect a light model to match the depth and accuracy of a flagship model on complex multi-step tasks

## Keep In Mind

- Model versions are regularly updated and individual models are replaced by newer versions over time, but the five categories (flagship, light, mid-tier, open source, specialist) remain stable and are the framework for making decisions
- A 2 million token context window allows you to input an entire book for analysis in a single prompt (relevant for Grok 4.1 and Gemini 3 Pro)
- Knowledge distillation allows light models like Gemini 3 Flash to retain 90–95% of flagship capability at a fraction of the cost and speed
- Claude Sonnet 4.5 is not just a "lesser Opus" — the speaker prefers it for its action-oriented, solution-focused tone compared to Grok's high-empathy style
- Kimi K2.5 performs well on Chinese language tasks, according to the speaker — for example, drafting a contract in Chinese with English explanations — in addition to English, making it useful for bilingual workflows
- Perplexity's hosted Kimi K2.5 is run on Perplexity's US servers — if you need full data control, download the open source version and run it locally
- Open source models can be turned into specialist models through fine-tuning, RAG systems, and custom tooling. Perplexity's Sonar research model is based on Llama 3.3 7B.

## Security & Safety Notes

- Never send sensitive data (financial statements, private emails, medical records, legal documents) through closed-source third-party platforms when an open source model can be run locally
- True data sovereignty means the model runs on your local machine or on infrastructure you control, with no data sent to third-party platforms. Only a locally downloaded and run model provides this level of control, according to the speaker.
- Understand where your model provider is hosted: Perplexity hosts Kimi K2.5 in the US, which has data jurisdiction implications depending on your location and the sensitivity of your data
- Multiple paid subscriptions to individual model APIs can become expensive — use a model aggregator to consolidate access and control costs
- When building AI agents that process personal data (emails, finances), prefer locally hosted open source models to avoid ongoing data leakage risk

## Common Pitfalls

- **Problem:** Using a flagship model for every task regardless of complexity, leading to unnecessary cost and slower results
  **Solution:** Default to a mid-tier model like Claude Sonnet 4.5 for everyday tasks. Only escalate to a flagship when the task requires multimodal capability, maximum code quality, or complex multi-step reasoning.

- **Problem:** Using a light model for a task that requires deep analysis, then being dissatisfied with the output quality
  **Solution:** Match the model to the time pressure. Use Gemini 3 Flash when speed is the priority. Use Gemini 3 Pro when you have time and need depth with specific evidence and numbers.

- **Problem:** Sending sensitive personal or financial data to closed-source platforms out of habit
  **Solution:** For any data you would not want exposed to a third party, download and run an open source model locally. This is free, private, and avoids per-query API costs on frequent tasks.

- **Problem:** Treating every new model release as a completely new decision, leading to choice paralysis
  **Solution:** Categorize new models into the five existing categories. If a new model is large, capable, and expensive, it belongs in the flagship category and follows the same selection rules as existing flagship models.

- **Problem:** Paying for multiple individual model subscriptions when a single aggregator would cover all needs
  **Solution:** Use Perplexity AI or a similar aggregator to access GPT-5.2, Claude Opus 4.6, Grok, Gemini, and Kimi through one subscription rather than maintaining separate paid access to each platform.

- **Problem:** Expecting a hosted open source model to provide the same privacy guarantees as a locally downloaded one
  **Solution:** A hosted open source model (for example, Kimi K2.5 on Perplexity) is still processed on third-party servers. Only a locally downloaded and run model provides true data sovereignty.
