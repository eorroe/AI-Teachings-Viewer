# You're Not Behind (Yet): A 30-Day Roadmap to Learn AI Prompting

## Glossary

- **AIM framework:** A prompt structure with three required components on separate lines: Actor (who the model should act as), Input (the context and data it needs), and Mission (what you want it to do).
- **Complete AIM-framework prompt:** A prompt that includes all three components — Actor, Input, and Mission — each on its own line, with the Actor specifying a persona, the Input providing attached documents or pasted context, and the Mission stating a precise, measurable outcome.
- **MAP framework:** A context-building structure with four components: Memory (conversation history or summaries from earlier sessions), Assets (files, data, or resources attached to the prompt), Actions (tools the model can call such as web search or code writing), and Prompt (the instruction itself informed by the other three).
- **OCEAN framework:** A taste-building structure with five components: Original (nonobvious angles), Concrete (specific names, examples, and numbers), Evident (visible reasoning and evidence), Assertive (a stance users can agree or disagree with), and Narrative (a story structure with hook, problem, insight, proof, and actions).
- **Top 10% of AI users:** Users who understand how AI thinks, how to structure effective prompts, and how to transform generic outputs into distinctive, high-quality work.
- **Expert-level prompting:** Applying structured frameworks like AIM and MAP, debugging prompts iteratively, steering outputs away from generic summaries toward original research-backed analysis, and verifying results rigorously.

## Overview

According to the speaker, this AI teaching provides a structured 30-day roadmap to master AI interaction and prompt engineering, moving from basic understanding to expert-level output quality. According to the speaker, the guide teaches you to communicate with AI through structured frameworks like AIM and MAP, debug your prompts iteratively, steer outputs toward expert-level quality, verify results rigorously, and develop personal taste in AI-generated content. According to the speaker, the goal is for you to have joined the top 10% of AI users—defined as users who understand how AI thinks, how to structure effective prompts, and how to transform generic outputs into distinctive, high-quality work—by the end of the 30 days.

## When to Follow These AI Teachings

- When you want to move from casual AI use to expert-level prompting in 30 days, according to the speaker
- When your AI outputs sound like generic LinkedIn posts or lack a distinctive voice
- When you need to get consistent, high-quality results from ChatGPT, Gemini, or Claude
- When you want to understand why AI produces problematic outputs and how to fix weak ones
- When you need to verify AI outputs for accuracy and avoid hallucinations
- When you want to develop a personal workflow for AI collaboration that you can apply to writing, analysis, coding, and research tasks

## Steps

### Step 1: Learn Machine English (Week 1)

Understand that AI models like ChatGPT and Gemini do not understand language like humans do. They predict the next likely token based on patterns in training data. Vague prompts produce vague outputs; sharp, targeted prompts produce sharp, targeted outputs. Treat prompting as structured communication, not casual conversation. Practice writing 5–10 prompts per day using the AIM framework until you can construct a complete Actor-Input-Mission prompt without referring to notes.

### Step 2: Use the AIM Framework for Every Prompt

Structure every prompt with three components:
- **Actor:** Tell the model who it is acting as (for example, "you are the world's most sought-after resume editor")
- **Input:** Provide the context and data it needs (for example, "I'm attaching my resume and the job description")
- **Mission:** State exactly what you want it to do (for example, "give me a bullet list of 10 specific ideas to improve clarity and measurable impact")

Write each component on a separate line. This structure helps the model compute your intent rather than guess at it. According to the speaker, outputs are at least five or 10 times better than before compared to vague one-line prompts.

### Step 3: Pick One AI Tool and Go Deep (Week 1)

Choose one foundational model and stick with it for the first week:
- **ChatGPT** for the most mature general-purpose experience
- **Gemini** if you work within Google's ecosystem
- **Claude** for business and project-based AI work

Do not jump between tools. Study its personality, cadence, limits, and strengths. The goal is to feel the rhythm of the model so you can transfer that intuition to other tools later. Use the AIM framework for every prompt you write during week 1, logging prompts by the end of the week to build muscle memory.

### Step 4: Build Context with the MAP Framework (Week 2)

Rich context produces better reasoning. Use the MAP framework to map what the AI needs:
- **Memory:** Include conversation history, previous notes, or summaries from earlier chat sessions. Repaste threads or ask the model to summarize before starting a new session to maintain continuity.
- **Assets:** Attach files, data, or resources that ground the model in reality. Copy-paste relevant documents, spreadsheets, or reference material directly into the prompt.
- **Actions:** Specify tools the model can call to do work, such as web search, file scanning, code writing, or document creation.
- **Prompt:** Write the instruction itself, informed by the memory, assets, and actions above.

According to the speaker, using MAP improves prompting results by providing richer context for the model to work with.

### Step 5: Debug Your Thinking (Week 2–3)

When output is weak, the fault is in your prompting, not the AI. Iterate systematically. Ask yourself: Did I get the right persona? Did I provide the right context? Did I give the right goal? You can even ask the model to explain its logic.

Use three cheat codes:
- **Chain of Thought:** Say "think step by step, show your reasoning, then give me the final concise answer"
- **Verifier Pattern:** Say "ask me three questions that would clarify my intent, one at a time, then combine what you learned and try again"
- **Refinement Pattern:** Say "before answering, propose two sharper versions of my question, ask which one I prefer"

Keep iterating on any weak output, each time adjusting one variable (persona, context, or goal), until you can articulate exactly why the final output works or identify the specific flaw in an off-target result.

### Step 6: Steer Toward Experts (Week 3)

Generic prompts produce generic, average outputs full of buzzwords. To get mastery-level results, steer the model away from the middle and toward the sharp edges of its training. Instead of vague prompts like "explain how to make a team more innovative," reference specific experts, frameworks, and research:
- Name sources like "Pixar's brain trust, Satya Nadella's strategy, and Harvard's research"
- If you do not know the experts, ask the model first: "list the top experts, researchers, research papers, and current thinking on black holes"
- Then feed that list back into a new prompt: "synthesize these sources into a framework that fills the current gap on the science of black holes"

This approach prevents the AI from repeating mainstream opinions and pushes outputs from generic summaries to original, research-backed analysis.

### Step 7: Verify Every Output (Week 3)

As the speaker notes, AI sounds just as confident when wrong as when right. Do not just consume output; critique it. Use five verification methods:
- **Assumptions:** Ask the model to list every assumption it made and rank each by confidence
- **Sources:** Ask it to cite two independent sources for each major claim, including title, URL, and a one-line quote
- **Counter Evidence:** Ask it to find one credible source that disagrees with the answer and explain the dependencies
- **Auditing:** Ask it to recompute every figure, show the math or code, and verify the numbers
- **Cross-Model Verification:** Run the same prompt in ChatGPT and Gemini or Claude, then ask one model to critique the other's output or verify the claims

By the end of week three, you will be able to apply all five verification methods to any output.

### Step 8: Develop Taste with the OCEAN Framework (Week 4)

The best AI outputs do not sound original; they sound like you. Move beyond generic results by using the OCEAN framework to add taste:
- **Original:** Look for nonobvious angles. If none exist, ask for three angles, label one as risky, and recommend the one the model likes most
- **Concrete:** Require specific names, examples, and numbers. Ask the model to back every claim with one real example
- **Evident:** Demand visible reasoning. Ask it to show logic in three bullets and provide evidence before the final answer
- **Assertive:** Require a stance that a user can agree or disagree with. Tell it not to pander, but to pick a side, state a thesis, defend it, and address the best counterpoint
- **Narrative:** Demand a story structure with a hook, problem, insight, proof, and actions

Treat AI as a sparring partner, not an answer machine. Run back-and-forth refinement rounds per output: present the draft, challenge one weakness, and ask for a revised version.

## Examples

### Example 1: Resume Review Prompt

**Before (vague):** "fix my resume"

**After (AIM framework):**
```
Actor: You are the world's most sought-after resume editor and business writer who has reviewed thousands of resumes that led to interviews at top tech companies.
Input: I'm attaching my resume and the job description for a senior product manager role at a fintech company.
Mission: Review it and give me a bullet list of 10 specific ideas on how to improve clarity, measurable impact, and alignment with the role to help me build the best resume that gets me hired.
```

### Example 2: Team Innovation Research

**Before (generic):** "Explain how to make a team more innovative"

**After (expert-steered):**
```
Actor: You are a management researcher specializing in organizational innovation.
Input: I lead a 20-person product team at a SaaS company. We have tried brainstorming sessions and hackathons with limited results.
Mission: Explain how to make my team more innovative using specific frameworks from Pixar's brain trust, Satya Nadella's growth mindset strategy, and Harvard Business School research. Provide three actionable experiments I can run this quarter.
```

### Example 3: Black Holes Research Synthesis

**Step 1**: "List the top 5 experts, researchers, research papers, and current thinking on black holes."

**Step 2**: Feed the results back into the model:
```
Actor: You are an astrophysics researcher synthesizing cutting-edge black hole science.
Input: Here are the top experts and papers:
Mission: Synthesize these sources into a framework that fills the current gap on the science of black holes, including three open questions the field is still debating.
```

## Best Practices

- Use the AIM framework for every prompt, with each component on a separate line
- Stick to one AI tool for the first week to build intuition before expanding
- Build context with MAP before asking for complex outputs
- Iterate on weak outputs by asking the model to explain its reasoning
- Verify factual claims with independent sources and cross-model checks
- Use the OCEAN framework to push outputs from generic to distinctive
- Treat AI as a sparring partner, not an answer machine
- Repaste conversation threads or summarize before starting new sessions to maintain memory
- Ask the model to list assumptions and rank them by confidence
- Run the same prompt across ChatGPT, Gemini, and Claude to cross-verify results

## Keep In Mind

- Prompting requires iteration, not a single attempt. Expect to refine weak outputs before reaching target quality.
- The performance gap between users who apply structured prompting and users who do not is widening as models become more capable.
- Deep skill with one AI tool transfers to others because all large language models operate on the same token-prediction principle.
- According to the speaker, by the end of week one, you should be able to write a complete AIM-framework prompt — a prompt that includes the Actor, Input, and Mission each on its own line — without referring to notes.
- The best outputs reflect your judgment and taste, not the model's default training distribution.

## Security & Safety Notes

- Never paste secrets, API keys, passwords, or sensitive personal data into AI prompts
- Treat all AI outputs as draft material requiring verification, not as authoritative truth
- Be aware that, as the speaker notes, AI can sound just as confident when wrong as when right
- Validate any figures, statistics, or code the AI generates by recomputing or auditing manually
- Cross-model verification is a safeguard, not a guarantee; always check primary sources when accuracy matters

## Common Pitfalls

- **Problem:** Using vague one-line prompts like "fix my resume"
  **Solution:** Apply the AIM framework with separate lines for Actor, Input, and Mission

- **Problem:** Jumping between 10 distinct AI tools in the first week
  **Solution:** Pick one tool, go deep, and learn its personality and limits before expanding

- **Problem:** Accepting generic outputs that sound like buzzword-filled LinkedIn posts
  **Solution:** Reference specific experts, frameworks, and research to steer the model toward mastery

- **Problem:** Assuming the AI is wrong when the output is weak
  **Solution:** Debug your own thinking by checking persona, context, and goal, then iterate

- **Problem:** Consuming AI output without verifying facts or figures
  **Solution:** Use the five verification methods: assumptions, sources, counter evidence, auditing, and cross-model verification

- **Problem:** Using AI as a vending machine that dispenses generic answers
  **Solution:** Treat AI as a sparring partner, push back on weak answers, and use the OCEAN framework to develop taste
