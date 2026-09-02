# You SUCK at Prompting AI (Here's the secret)

## Overview

Prompting AI is not asking questions — it is programming the model with words by calling it to action with enough structure, persona, context, and output requirements that it can predict the right completion instead of guessing. This teaching synthesizes NetworkChuck's video into prompting techniques including persona assignment, context provision, permission to fail, output requirements, few shot examples, chain of thought, extended thinking, trees of thought, and adversarial validation, and the underlying skill behind them: the ability to define exactly what you want the model to produce before typing the prompt. NetworkChuck frames poor AI responses as a prompt design issue: "If the AI model's response is bad, I'm like treat everything as like a personal skill issue. The problem is me."

## When to Follow These AI Teachings

- When an AI returns generic, vague, or hallucinated results
- When you need consistent tone, format, or accuracy across outputs
- When building prompts for APIs, system prompts, or repeatable AI workflows
- When you want to reduce hallucinations and increase reliability
- When you need to produce structured content such as emails, reports, or summaries

## Steps

### Step 1: Adopt the correct mindset

Treat every prompt as a program, not a question. Large Language Models (LLMs) are prediction engines trained to complete patterns. NetworkChuck observes that vague prompts lead to generic outputs: "if your pattern is vague, the AI guesses anything." Before typing, clarify exactly what you want the model to do.

### Step 2: Assign a persona

Tell the AI who it is. Specify the role, expertise, and audience it should write for. Example: "You are a senior site reliability engineer at CloudFlare writing to both CloudFlare customers and engineers." This narrows the knowledge source and improves tone and focus.

### Step 3: Provide full context

Give all facts, background, and constraints the model needs. Do not assume the AI knows what happened or what you want. Include dates, events, budgets, audience details, stakeholder names, project timelines, and technical constraints. Providing complete facts and constraints directly reduces the chance that the model hallucinates missing details.

### Step 4: Give permission to fail

Explicitly tell the AI it can say "I don't know" if the answer is not in the context. Without this instruction, the model will guess to please you, which increases hallucinations.

### Step 5: Define output requirements

Specify length, tone, structure, format, and any constraints. Example: "Keep it under 200 words, professional, with a bulleted timeline, under 200 words with a professional, apologetic, radically transparent tone and no corporate fluff." The more specific the output requirements, the more predictable the result.

### Step 6: Use few shot examples

Provide examples of the exact style, tone, or structure you want. Show, do not just describe, the desired output. Few shot prompting teaches the model the pattern directly and reduces guesswork.

### Step 7: Apply Chain of Thought (COT)

Add "Think through this step by step before answering" or list the explicit steps the model should follow in its reasoning process. This requires the model to show its work before producing a final answer, which increases accuracy and lets you inspect its logic.

### Step 8: Enable Extended Thinking in Supported Models

Claude (via the "extended thinking" toggle) and Gemini (via "thinking" mode) both support extended thinking or reasoning modes. Enable these for tasks that require verifying calculations, comparing options, evaluating tradeoffs, or analyzing data where a single reasoning pass misses errors.

### Step 9: Use Trees of Thought (TOT) for complex problems

Ask the model to generate three distinct tonal approaches, evaluate each against criteria of radical transparency, customer empathy first, and future-focused assurance, and synthesize the best one.

### Step 10: Run adversarial validation (playoff method)

Generate competing drafts from different personas, have one persona critique the others, then collaborate on a final version. Example: engineer and PR crisis manager write drafts, an angry customer critiques both, then they produce a final email together. NetworkChuck observes that "AI is normally better at critiquing or editing than original writing."

### Step 11: Build a Prompt Library and Clarify Intent Before Prompting

Save successful prompts. If you are stuck, describe exactly how you want the output to work before typing the prompt. If you cannot explain it clearly yourself, you can't prompt it. Use a prompt enhancer only after your own thinking is clear.

## Examples

### Example 1: CloudFlare outage apology email

Bad prompt: "Write an apology email for CloudFlare."

Improved prompt with persona, context, output requirements, and permission to fail: "You are a senior site reliability engineer at CloudFlare writing to both CloudFlare customers and engineers. Context: CloudFlare experienced an outage that impacted 20 percent of internet traffic. We are still reviewing root cause. Keep the email under 200 words, professional, with a bulleted timeline, under 200 words with a professional, apologetic, radically transparent tone and no corporate fluff. If any detail is not confirmed, say so explicitly rather than guessing."

### Example 2: Brainstorming with Trees of Thought

Prompt: "Brainstorm three distinct tonal strategic approaches to this customer communication. Evaluate each approach, then synthesize them into one final recommended email."

### Example 3: Adversarial validation for email quality

Prompt: "Round one: Write an apology email as a CloudFlare engineer. Write a second version as a PR crisis manager. Round two: Switch to an angry customer persona and critique both drafts brutally. Round three: Collaborate as the engineer and PR manager to produce one final email that addresses the customer's feedback."

## Best Practices

- ✅ Treat prompting as programming with words, not asking questions
- ✅ Assign a clear persona with specific expertise and audience
- ✅ Provide all context, facts, and constraints in every prompt
- ✅ Explicitly grant permission to say "I don't know"
- ✅ Specify exact output requirements: length, tone, format, and structure
- ✅ Use few shot examples to show desired patterns
- ✅ Use Chain of Thought for accuracy and transparency
- ✅ Enable extended thinking or reasoning models for complex tasks
- ✅ Use Trees of Thought or adversarial methods for high-stakes outputs
- ✅ Save successful prompts into a prompt library
- ✅ Clarify your own thinking before you prompt

## Keep In Mind

- LLMs do not know what you know. They do not remember prior conversations reliably. Always provide full context.
- LLMs have training data cutoffs and cannot access real-time information without web search or tool integrations.
- The video argues that LLMs are designed to provide an answer even when uncertain. Without permission to fail, they will hallucinate rather than say they do not know.
- As Dr. Jules White explains in the video, LLMs don't think like humans; they are prediction engines.
- Memory features in chat interfaces can create a false sense of shared context. Do not assume the model knows your project, preferences, or history.

## Security & Safety Notes

- Do not paste secrets, API keys, passwords, or sensitive credentials into prompts.
- When enabling web search or external tools, cross-check returned facts against trusted primary sources. Models retrieve outdated, biased, or incorrect information from indexed sources.
- Treat AI-generated content as a first draft, not a finished product. Review facts, especially for legal, medical, financial, or safety-critical decisions.
- If you are using AI in customer-facing or regulated environments, add human review before publishing outputs.

## Common Pitfalls

- **Problem:** Vague prompts produce generic or wrong outputs.
  **Solution:** Add a persona, full context, and explicit output requirements.
- **Problem:** The AI hallucinates details or events.
  **Solution:** Provide complete context, tell the AI it can say "I don't know," and verify facts with external sources.
- **Problem:** The AI assumes it knows what you want.
  **Solution:** Always provide all context every time. Do not rely on chat memory.
- **Problem:** Outputs are inconsistent across prompts.
  **Solution:** Use few shot examples and explicit output requirements.
- **Problem:** The AI produces generic, vague, or hallucinated outputs, leading to frustration.
  **Solution:** Recognize it as a prompt design issue. Stop, write out what you want clearly, then prompt again.

## Glossary

- **Agent mode**: A mode in ChatGPT Atlas where the AI watches entire videos and performs tasks like finding specific moments or answering detailed questions about video content.


(End of file - total 122 lines)
