# Why do AI models hallucinate?

## Overview

This AI teaching explains the phenomenon of hallucinations: why AI models like Claude generate confident but incorrect information. It covers the underlying causes—including, as Anthropic explains, cases where when you ask about something obscure like specific research papers from a researcher with fewer than 100 citations on Google Scholar, there just is not enough information for the AI to draw from, so it tries to be helpful and takes a guess that is sometimes wrong. It also covers the broader pattern where AIs are trained to be helpful and want to give you some answer even when they are not sure, which can lead to fabricating information instead of admitting uncertainty. The teaching also covers techniques Anthropic uses to reduce hallucinations during training and testing, such as training Claude to be honest and to say "I don't know" when it is not sure. It also provides concrete, actionable steps you can use to spot and avoid hallucinations when using AI assistants.

## When to Follow These AI Teachings

- When using AI assistants for factual research or information gathering
- When asking about obscure, niche, or current topics
- When you need specific facts, statistics, or research citations
- When working with information about real but not widely known people or places
- When you need exact details such as dates, names, or numbers
- When the answer will inform critical decisions or work

## Steps

### Step 1: Ask the AI to provide and verify sources

Ask the AI to find sources that back up its claims. If it already provided sources, ask it to check that those sources actually exist and support what it is saying.

### Step 2: Tell the AI it is okay to say "I don't know"

When starting a conversation, tell the AI upfront that it is acceptable to admit uncertainty. This removes the pressure on the model to fabricate an answer instead of acknowledging a gap in its knowledge.

### Step 3: Ask the AI to assess its own confidence

After receiving an answer, ask the AI to rate its confidence on a scale of 1 to 10 and list the three specific facts in its response it is least certain about. As Anthropic notes in the video: "Often the AI knows it's wrong, but just wanted to sound confident." Prompting it explicitly to assign a numeric confidence score and identify weak points surfaces that uncertainty.

### Step 4: Re-ask the answer in a new chat to find errors

If you have an answer you are unsure about, start a completely new chat session (do not continue the existing thread) and ask the AI to fact-check the original answer by: (1) verifying every named source, statistic, or citation, (2) flagging any claim that does not have a verifiable source, and (3) listing any internal contradictions between statements in the original response.

### Step 5: Cross-reference with trusted sources

When accuracy matters—such as for academic or scientific claims, legal or regulatory decisions, financial data, or general news—independently verify the AI's claims against independent sources appropriate to the domain. Be especially careful with specific numbers, dates, and citations — these are the most common hallucination targets.

### Step 6: Ask follow-up questions if something sounds off

If any part of the AI's response contains claims that contradict known facts, internal inconsistencies between earlier and later statements in the same response, or specific numbers such as "12.4 percent aquaculture growth in 2023" without a cited source, ask the AI targeted follow-up questions such as: "Show me the exact source URL for the 2023 aquaculture growth figure," "Walk me through the chain of reasoning that leads to that conclusion," or "What is the original study or dataset this number comes from?" Do not accept a vague reference like "industry reports" — ask for a specific title, author, URL, or publication date.

## Examples

### Example 1: Verifying obscure research citations

You asked Claude to list papers written by a researcher with fewer than 100 citations on Google Scholar. Claude confidently returned three paper titles. None of those titles actually existed. By asking Claude to verify its sources in a new chat, or by cross-checking against Google Scholar, Semantic Scholar, or arXiv, you can catch this type of hallucination before relying on the information.

### Example 2: Checking statistics and facts

You asked the AI for the percentage growth rate of the commercial aquaculture industry in 2023. The AI produced the figure 12.4 percent with confidence, citing "a 2023 industry report." By asking the AI to name the exact report title, publisher, and page number — and then checking whether that report actually exists and contains that figure — you can confirm whether the statistic is real or fabricated.

### Example 3: Confirming details about little-known people

You asked about the background of a real but not widely known software engineer at a mid-sized company. The AI generated plausible but false biographical details, including a nonexistent university degree and a previous employer that does not appear on the person's LinkedIn profile. Asking the AI to rate its confidence on a 1-to-10 scale, or starting a new chat and asking it to fact-check its own earlier answer by verifying each named institution and employer, helps expose the error before you act on it.

## Best Practices

- ✅ Ask the AI to find sources to back up its claims.
- ✅ Ask the AI to verify that its existing sources actually support what it is saying.
- ✅ Tell the AI upfront that it is okay to say "I don't know."
- ✅ Ask the AI how confident it is and whether anything might be wrong.
- ✅ For answers you are unsure about, start a new chat and ask the AI to find errors and confirm sources.
- ✅ Cross-reference critical information with trusted external sources.
- ✅ Be skeptical and double-check specific numbers, dates, and citations.
- ✅ Ask follow-up questions if something sounds off.
- ❌ Don't assume an AI answer is correct simply because it sounds confident.
- ❌ Don't skip verification.
- ❌ Don't accept citations or statistics without checking that they exist and support the claim.

## Keep In Mind

- Hallucinations occur when asking for specific facts, statistics, or citations.
- Hallucinations occur on obscure, niche, or very recent topics—for example, when asked about specific research papers from a researcher with fewer than 100 citations.
- Hallucinations occur when asking about real but not widely known people or places—for example, a software engineer at a mid-sized company.
- Hallucinations occur when exact details such as dates, names, or numbers are required.
- The wrong answer often looks like it could be the right one, making hallucinations hard to catch.
- Reducing hallucinations is an ongoing challenge for the entire AI field and is not a solved problem.

## Security & Safety Notes

- Fabricated citations, statistics, and source URLs are common hallucination vectors—meaning they are frequent ways hallucinations manifest—and are specifically designed to look authoritative. Always verify the existence of every cited source before sharing AI output with others.
- Confident but incorrect AI responses mislead users into making poor decisions, especially in medical, legal, financial, and academic contexts where the cost of acting on false information is high.
- Verify AI-generated facts, figures, and citations against independent sources before incorporating them into reports, decisions, or external communications.
- Treat AI outputs as unverified claims rather than authoritative facts in contexts where the cost of acting on false information is high—such as legal arguments, medical advice, financial modeling, academic research, and compliance documentation.

## Common Pitfalls

- **Problem:** The AI gives a confident-sounding but incorrect answer about an obscure topic — for example, fabricating paper titles for a researcher with fewer than 100 citations. **Solution:** Tell the AI upfront it is okay to say "I don't know," then cross-reference every named source with Google Scholar, Semantic Scholar, or arXiv before relying on the information.

- **Problem:** The AI cites non-existent papers, statistics, or sources — for example, producing a precise figure like "12.4 percent aquaculture growth in 2023" with a vague reference to "an industry report" that does not exist. **Solution:** Ask the AI to name the exact report title, publisher, and page number for every citation, then independently confirm each one through the publisher's website or a searchable database.

- **Problem:** The AI presents false information as fact because it is trained to prioritize being helpful and sounding confident over admitting uncertainty. **Solution:** Explicitly invite uncertainty by telling the AI it is okay to say "I don't know," then ask it to rate its confidence on a 1-to-10 scale and identify the three facts it is least certain about before you rely on any part of its response.
