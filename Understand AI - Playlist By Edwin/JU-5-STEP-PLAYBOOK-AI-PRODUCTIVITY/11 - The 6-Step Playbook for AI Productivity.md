# The 6-Step Playbook for AI Productivity

## Overview

This AI teaching provides a structured playbook for transforming AI from a generic assistant into a consistent, high-quality collaborator. The speaker describes AI as "a super eager, super enthusiastic intern who's tireless, who's capable, who will do a bunch of work, but they're not really great at pushing back. They're not really great at setting boundaries." It teaches six foundational prompt engineering techniques — context engineering, chain of thought reasoning, few shot prompting, reverse prompting, role assignment, and difficult conversation simulation — combined with practical workflows for preserving critical thinking. The core premise is that AI cannot read your mind, so you must make implicit expectations explicit, provide concrete examples, and treat the model like an eager intern who needs clear boundaries and permission to ask questions.

## When to Follow These AI Teachings

- When you need AI to produce work that matches your voice, brand, or specific standards rather than generic internet-style output
- When preparing for high-stakes conversations such as performance reviews, salary negotiations, or difficult feedback
- When AI outputs seem off-brand, inaccurate, or unreliable and you need to diagnose why
- When you want to preserve or strengthen your own critical thinking rather than offload cognitive work
- When working with AI on tasks that require specific data, context, or examples you have not yet shared
- When you need to evaluate not just the output but the reasoning behind the output

## Steps

### Step 1: Practice Context Engineering

Context engineering is gathering every piece of information an AI model needs before you submit a prompt. Before asking AI to perform a task, collect brand voice guidelines, customer call transcripts, product specifications, past examples of your own writing, and any data points relevant to the task. Do not leave anything implicit. The speaker's test for context engineering is: "Write down your prompt and whatever documentation you provide to an AI and then walk down the hall and give it to a human colleague. If they cannot do the thing you're asking for, you shouldn't be surprised that AI can't do it."

### Step 2: Enable Chain of Thought Reasoning

Append one additional sentence to every important prompt: "Before you respond to my query, please walk me through your thought process step by step." This forces the model to externalize its reasoning before generating the final answer. Because large language models generate text one word at a time, asking for a step-by-step walkthrough bakes the model's reasoning into its own response, leading to more accurate, transparent, and auditable outputs. This also lets you evaluate the assumptions behind the answer, not just the answer itself.

### Step 3: Apply Few Shot Prompting with Good and Bad Examples

AI is an exceptional imitation engine. Identify five of your best examples of the output you want — emails you are proud of, reports that hit the mark, messages that sound like you — and include them in your prompt. If you can only think of a bad example, ask AI to generate a good example of the desired output and explain why your bad example fails to meet it. Providing concrete examples is far more effective than using adjectives like "professional" or "concise." Pairing a good example with a bad example teaches the model both what to emulate and what to avoid.

### Step 4: Use Reverse Prompting to Surface Missing Information

Before AI begins generating, give it permission to ask questions. Add this instruction to your prompt: "Before you get started, ask me for any information you need to do a good job." Without this permission, AI will guess, hallucinate numbers, or insert placeholder text rather than trouble you with questions. Reverse prompting turns AI from a passive order-taker into an active teammate that clarifies requirements before acting, dramatically reducing wasted iterations and incorrect outputs.

### Step 5: Assign a Role to Focus the Model's Knowledge

Tell AI who it should be for this task. Roles like "professional communications expert," "Dale Carnegie," "a skeptical journalist," or "a molecular biologist" trigger the model to draw on knowledge patterns associated with that role. Instead of saying "review this correspondence," say "I'd like you to take on the mindset of Dale Carnegie. How would he think about this message?" You can also use roleplay constraints like "How would Jerry Seinfeld solve this problem?" or "How would Amazon approach this?" to combine different knowledge sources and generate novel perspectives.

### Step 6: Simulate Difficult Conversations Before They Happen

For high-stakes conversations, set up three parallel chat sessions: a personality profiler to map the other person's communication style and motivations, a roleplay character embodying that person to practice the conversation, and a feedback giver to grade your performance. Run through the conversation in the roleplay window, capture the transcript, upload it to the feedback giver, and iterate on your approach. This three-window setup creates a safe rehearsal environment for difficult conversations, letting you fail safely and refine your messaging before the real interaction.

## Examples

### Example 1: Writing an On-Brand Sales Email

Context engineering: Upload your brand voice guideline, a transcript of a recent customer call, and the product specifications mentioned in that call. Chain of thought: Add "walk me through your thought process step by step." Few shot: Include two of your best past sales emails as examples. Reverse prompting: Add "ask me for any information you need before you begin." Role assignment: Instruct the model to write as a professional communications expert following Dale Carnegie principles. The result is an email that references the actual customer discussion, matches your voice, and avoids generic filler.

### Example 2: Preparing for a Commission Dispute Conversation

Personality profiler: Describe the other person's communication style, known motivations, and best-case outcome. Roleplay: Instruct a fresh chat window to embody that person with specific behaviors drawn from your personality profiler output, then practice the conversation. Feedback giver: Upload the conversation transcript and ask for a grade out of 100, specific strengths, specific weaknesses, and a one-page conversation guide ordered by likely talking point sequence. Iterate two or three times until the feedback shows you are ready.

### Example 3: Enforcing Critical Thinking

Add a custom instruction such as: "I am trying to stay a critical and sharp analytical thinker. Whenever you see opportunities in our conversations, please push my critical thinking ability." To make feedback more honest, instruct the model to "do your best impression of a cold war era Russian Olympic judge. Be brutal. Be exacting. Deduct points for every logical inconsistency, unsupported claim, or factual error." This counters AI's default tendency to be agreeable.

## Best Practices

- ✅ Make all context explicit. Upload files, paste data, and provide examples rather than assuming AI can infer your intent.
- ✅ Use the humanity test. If a human colleague cannot complete the task from your prompt and attached materials, refine the inputs.
- ✅ Ask AI to think out loud before answering by adding one sentence to every important prompt.
- ✅ Provide both good and bad examples to teach the model what to emulate and what to avoid.
- ✅ Give AI explicit permission to ask clarifying questions before it begins working.
- ✅ Assign a specific role or persona to focus the model's knowledge retrieval and connection-making.
- ✅ Treat AI as a teammate, not a search engine. Instruct it, iterate with it, and ask it to reconsider.
- ✅ Use three chat windows to separate profiling, roleplay, and feedback for complex interpersonal tasks.

## Keep In Mind

- AI is predisposed to say yes because it has been instructed to be a helpful assistant. The speaker says AI "will tell you that you did a good job even when you didn't, saying 'Great job, buddy' without meaning it, unless you explicitly instruct it to be critical and exacting."
- According to the speaker, AI demonstrates cognitive biases including anchoring (over-relying on the first piece of information it receives), confirmation bias (favoring evidence that matches its initial assumption), and overconfidence (presenting uncertain outputs as if they were certain). Treat its outputs as starting points for judgment, not as authoritative conclusions.
- AI has good intentions but technical limitations. When you recognize that it is super eager and enthusiastic, tireless and capable, and will do a lot of work but not great at pushing back or admitting uncertainty, you will iterate more, ask it to try again, and get better results.
- The primary limitation of AI is not the technology but human imagination. Mastery comes from exercising these techniques consistently, not from knowing them once.

## Security & Safety Notes

- Do not upload confidential customer data, financial figures, or proprietary information into AI tools without confirming your organization's data handling policies.
- Always verify AI-generated numbers, dates, and factual claims against primary sources. AI will guess when it lacks data.
- When using reverse prompting, be prepared for AI to ask for sensitive information. Evaluate whether sharing that information is appropriate before responding.
- Treat AI-generated drafts as unclassified and unaudited. Review all outputs before sending them externally or basing decisions on them.

## Common Pitfalls

- **Problem:** AI output sounds generic or does not match your voice.
  **Solution:** You have not practiced context engineering. Upload your brand guidelines, past writing samples, and explicit instructions about tone and audience.

- **Problem:** AI hallucinates numbers, names, or facts.
  **Solution:** You did not provide the underlying data and did not enable reverse prompting. Supply the actual figures and instruct the model to ask before guessing.

- **Problem:** AI agrees with everything you say and gives unhelpful praise.
  **Solution:** You have not instructed it to push back. Use the critical thinker custom instruction or the brutal judge persona to force honest feedback.

- **Problem:** AI gives long, verbose answers when you need brevity.
  **Solution:** Include a concise example of the length and style you want, and explicitly state the desired format, word count, or structure in your prompt.

- **Problem:** You get the same mediocre output every time.
  **Solution:** You are iterating on a single prompt. Run three parallel chat windows with different roles or constraints, compare the outputs, and synthesize the best elements.

- **Problem:** You spend more time prompting than the task is worth.
  **Solution:** Build reusable prompt templates and custom GPTs for repetitive tasks. Save your best few-shot examples, brand context, and role instructions so you do not rebuild them from scratch every time.

## Glossary

- **Chain of thought reasoning**: A technique where you ask the model to externalize its reasoning before generating the final answer. The speaker says: "Before you respond to my query, please walk me through your thought process step by step." This bakes the model's reasoning into its own response.
- **Context engineering**: Gathering every piece of information an AI model needs before submitting a prompt. The speaker's test: "Write down your prompt and whatever documentation you provide to an AI and then walk down the hall and give it to a human colleague. If they cannot do the thing you're asking for, you shouldn't be surprised that AI can't do it."
- **Few shot prompting**: Providing examples of the exact style, tone, or structure you want the AI to match. The speaker says: "If you don't give an example, it imitates the internet, but it doesn't do much more than that."
- **Reverse prompting**: Giving the AI permission to ask questions before it begins generating. The speaker says: "Before you get started, ask me for any information you need to do a good job."
- **Role assignment**: Telling the AI which role or expert perspective to adopt. The speaker says: "You are forcing the model to access a specific set of vocabulary and expertise."
