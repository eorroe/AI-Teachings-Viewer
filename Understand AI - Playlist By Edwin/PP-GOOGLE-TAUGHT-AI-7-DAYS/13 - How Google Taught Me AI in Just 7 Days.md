# How Google Taught Me AI in Just 7 Days

## Overview

According to the speaker, this AI teaching distills the speaker's experience with Google's 8-hour AI course into a framework for interacting with AI tools effectively. It teaches a structured prompting method called PACE (Provide context, Ask specifically, Cue with examples, Evaluate and iterate), explains critical failure modes like hallucinations and knowledge cutoffs, and covers how to maintain human oversight, recognize AI bias, and stay current with AI developments. The goal is to move from trial-and-error prompting to a repeatable system.

## When to Follow These AI Teachings

- When drafting documents, marketing copy, code, or proposals using AI
- When making decisions based on AI-generated output such as investment research, contracts, or hiring materials
- When building products or features that rely on AI-generated content or recommendations
- When you need to evaluate AI output for accuracy, bias, or relevance
- When trying to improve prompt quality for complex reasoning, data analysis, or multi-step creative work
- When you want to stay informed about AI tool changes without information overload

## Steps

### Step 1: Provide Context

Give the AI relevant background before asking for output. Include your situation, audience, constraints, budget, and the goal behind your request. A prompt like "Give me generic marketing ideas" produces suggestions with no relevance to your product, audience, or constraints. A prompt like "I'm launching a productivity app for freelancers. My budget is limited, and I need marketing ideas that don't require paid ads" gives the AI actual constraints to work within. The more relevant background you include, the less the AI has to guess. Different prompts with different levels of specificity produce different results.

### Step 2: Ask Specifically

Choose a precise verb and specify the output format. Different verbs produce different results: "Summarize this report" gives a condensed version, "Compare these two reports" gives analysis, and "Turn this report into action items" gives a task list. If you want a timeline, ask for one. If you need pros and cons in a table, say so. If you want short punchy sentences instead of dense paragraphs, state that explicitly.

### Step 3: Cue With Examples

Use one-shot or few-shot prompting to show the AI the pattern you want. Instead of writing a long paragraph describing tone and length, write one example yourself, paste it in, and tell the AI to write the rest like this. For example, write one team bio yourself, then ask the AI to write the remaining bios in the same style. Providing two or three examples locks in the style without confusing the model. Providing more than three examples adds noise rather than clarity.

### Step 4: Evaluate and Iterate

Treat prompting as a back-and-forth conversation instead of a single request. Start with a draft, review what you get back, identify what is missing, and refine your ask. Once you have iterated to a result that meets your original requirements, ask the AI to write a single prompt that would recreate that output from scratch. This reveals what actually mattered in your iterations and helps you prompt better next time.

### Step 5: Use Chain of Thought Prompting for Complex Logic

For tasks involving calculations, scheduling, troubleshooting, or multi-layer analysis, ask the AI to show its work before giving the final answer. Instead of asking "When will this project finish?" ask the AI to list the tasks, identify dependencies, calculate the sequence, and then tell you the finish date. This step-by-step reasoning reduces errors compared to asking for the answer directly.

### Step 6: Maintain Human in the Loop

Never copy AI output directly without review. Ask the AI for a draft, review it against what you actually need, adjust requirements or tone, and make the final call on what gets published or used. For high-stakes outputs like contracts, investment decisions, or hiring materials, the speaker warns that blind trust in AI output for consequential use cases scales negative consequences quickly.

### Step 7: Recognize AI Failure Modes

Understand two specific ways AI fails even with perfect prompting. Knowledge cutoffs: every model has a training date and does not know events after that point. Hallucinations: instead of saying "I don't know," the AI fabricates plausible-sounding citations, statistics, or events. Hallucinations can be obvious or subtle. Subtle hallucinations like citing a nonexistent research study are the most dangerous because they are hard to catch.

### Step 8: Understand AI Bias

Recognize two main types of AI bias. Quality of service harm: the AI works well for one group but poorly for another, such as voice assistants trained on American English struggling with different accents. Representation harm: the AI reflects and amplifies societal biases in its training data, such as generating a higher proportion of men for "scientist" prompts and a higher proportion of women for "receptionist" prompts. Both issues trace back to who builds the tools and what data they are trained on.

### Step 9: Stay Current With Two Sources

AI tools and capabilities evolve substantially by the end of the year. For example, consistent character generation across images went from a manual, error-prone process to an automated feature within a year, and AI video generation shifted from glitchy, unusable output to cinematic-quality clips with native audio over a couple months. Pick two reliable sources and stick with them instead of trying to follow every headline. For newsletters, use Ben's Bites for daily updates or The Rundown AI for quick summaries. Check in regularly so you do not miss major shifts like new consistency features or improved video generation.

## Examples

### Example 1: Job Posting With Human in the Loop

Instead of asking AI to write a job posting and copying it directly, ask for a draft first. Review it against your actual role requirements, adjust the tone and responsibilities, ask for revisions if needed, and approve the final version yourself. This prevents attracting the wrong candidates due to AI-generated inaccuracies or generic language.

### Example 2: Marketing Ideas for a Productivity App

Use context and specificity: "I'm launching a productivity app for freelancers. My budget is limited, and I need marketing ideas that don't require paid ads." This produces constrained, usable ideas. Compare that to "Give me some marketing ideas," which returns generic advice with no relevance to your actual situation.

### Example 3: Team Bios Using One-Shot Prompting

Write one team bio yourself with your desired tone and length. Paste it into the prompt and tell the AI to "write the rest like this." The AI closely follows the pattern you provide without needing detailed style instructions. Provide two or three bios as examples if you want to lock in the style further.

### Example 4: Project Finish Date Using Chain of Thought

Instead of asking "When will this project finish?" ask the AI to list the tasks, identify the dependencies, calculate the sequence, and then tell you the finish date. The step-by-step breakdown produces a more accurate estimate than asking for the final date directly. Apply the same approach to technical troubleshooting or financial calculations.

### Example 5: Detecting Subtle Hallucinations

If the AI cites a research study or provides statistics, verify the source exists and the numbers are accurate before using them in decisions. Subtle hallucinations like a fabricated study citation sound credible but can cause real problems in reports, proposals, or contracts.

## Best Practices

- ✅ Provide context about your audience, constraints, and goal before asking for output
- ✅ Use specific verbs like summarize, compare, or turn into action items
- ✅ Specify the format you want, such as a table, timeline, or bullet list
- ✅ Give two or three examples when you need a specific tone or structure
- ✅ Treat prompting as an iterative conversation and refine your requests
- ✅ Ask the AI to show its work for calculations, scheduling, or multi-step reasoning
- ✅ Review all AI output against your actual requirements before using it
- ✅ Verify citations, statistics, and factual claims before relying on them
- ✅ Pick two reliable AI news sources and check them regularly
- ✅ Understand that AI reflects training data patterns, not objective truth

## Keep In Mind

- AI works by recognizing patterns in training data, not by reasoning like a human
- Every model has a knowledge cutoff and cannot reliably answer questions about events after its training date
- Hallucinations can be subtle, such as fake citations or fabricated statistics that sound plausible
- AI bias reflects the training data and the people who built and trained the tool, not neutral facts
- The tools and capabilities available today evolve substantially by the end of the year as providers release new models, features, and pricing structures. For example, consistent character generation across images went from a manual, error-prone process to an automated feature within a year, and AI video generation shifted from glitchy, unusable output to cinematic-quality clips with native audio over a couple months.
- A well-structured prompt generally produces better results than a longer but disorganized one, since the difference comes from structure, not length
- The PACE method works for standard prompting tasks, but techniques such as chain-of-thought prompting are needed for complex multi-step work.

## Security & Safety Notes

- Do not input confidential business data, personal identifiable information (names, addresses, financial records), or sensitive credentials (API keys, passwords) into cloud-hosted AI tools such as ChatGPT, Claude, or Gemini unless your organization's data handling policy explicitly permits it.
- Verify all factual claims, citations, and statistics before using them in contracts, reports, or investment decisions
- Be aware that AI output reflects gender, racial, or cultural biases present in training data
- Review AI-generated content for harmful stereotypes before publishing or distributing
- Treat AI as a collaborator, not an authority. Human oversight is required for high-stakes decisions
- Knowledge cutoffs mean AI cannot provide real-time information about recent events, laws, or market conditions

## Common Pitfalls

- **Problem:** Asking vague questions without context, resulting in generic or irrelevant output
  **Solution:** Always include your situation, audience, constraints, and goal in the prompt

- **Problem:** Using the wrong verb, which produces the wrong type of output
  **Solution:** Choose a precise action verb like summarize, compare, analyze, or rewrite that matches the result you need

- **Problem:** Trusting AI output without review, leading to hallucinations or bias entering your work
  **Solution:** Apply human in the loop review for every output, especially in high-stakes scenarios

- **Problem:** Asking for recent information that falls after the model's training cutoff
  **Solution:** Verify the model's knowledge cutoff date and use current sources for time-sensitive facts

- **Problem:** Assuming AI-generated content is objective or unbiased
  **Solution:** Test outputs for representation bias and quality of service gaps across different user groups

- **Problem:** Overloading yourself with AI news and updates
  **Solution:** Stick to two trusted sources instead of chasing every headline or trend

- **Problem:** Writing long, disorganized prompts expecting better results
  **Solution:** Use the PACE structure: context first, then a specific ask, then examples, then iterative refinement
