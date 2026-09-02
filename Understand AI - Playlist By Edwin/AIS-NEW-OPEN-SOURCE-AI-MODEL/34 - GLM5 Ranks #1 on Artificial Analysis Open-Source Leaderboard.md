# GLM5 Ranks #1 on Artificial Analysis Open-Source Leaderboard

## Overview

GLM5 by Z AI is currently the top-ranked open-source model on the third-party Artificial Analysis leaderboard, delivering performance on par with top closed models like Claude Opus 4.5 and GPT 5.2, according to benchmark comparisons in the video. It supports an Agent mode capable of executing multi-step tasks—including coding full interactive web applications, analyzing documents, and generating multimedia content—all from a single prompt. This teaching walks through how to access GLM5, when to use Agent mode versus regular Chat, and how to leverage its multimodal capabilities for real-world tasks.

## When to Follow These AI Teachings

- When you need an AI model to build multi-file or multi-page projects (courses, apps, games) from a single prompt
- When you need to analyze uploaded documents (PDFs, spreadsheets, CSVs) and generate structured outputs like charts, spreadsheets, or reports
- When you want to generate interactive HTML simulations, games, or visualizations with adjustable parameters
- When you need an open-source model for factually accurate information, such as law or medical research
- When comparing open-source models for coding, research, or agentic tasks

## Steps

### Step 1: Access GLM5

1. Navigate to `https://z.ai` in your browser.
2. Locate the chat interface at the top of the page.
3. Select the latest GLM5 model from the model selector before entering any prompt.

### Step 2: Choose Agent Mode or Regular Chat

- **Agent Mode:** Toggle this on for complex, multi-step tasks. The model will automatically generate a to-do list, plan the work, execute it step by step in a sandbox environment, and produce a final polished result. Use this when you need multiple pages, files, or coordinated outputs.
- **Regular Chat:** Use this for single-step tasks that do not require multi-file output. This mode generates one output at a time and is sufficient for single-answer Q&A, single-file code generation, or single-output analysis.

### Step 3: Prompt for Multi-Page or Multi-File Projects

1. In Agent mode, write a single descriptive prompt that specifies what you want built, what format the output should be in (e.g., "standalone HTML file," "Excel spreadsheet with multiple tabs"), and any required features.
2. Press **Generate**.
3. Review the to-do list the model produces, then wait for it to complete all steps in the sandbox.
4. Open the generated output in a new tab or download it (for spreadsheets) to verify completeness.
5. When refinement is required, send follow-up prompts to refine specific aspects (e.g., "fix the lighting so it actually changes with the time of day," "add a moving average indicator").

### Step 4: Analyze Uploaded Documents

1. In either Chat or Agent mode, upload at least one document (PDF, CSV, image, or text file) using the file upload button.
2. In your prompt, specify the desired output format (e.g., "make a consolidated spreadsheet with financials, charts, growth forecasts, and recommendations").
3. Use Agent mode when the task requires multiple steps (parsing multiple files, generating multiple tabs, computing charts).
4. Download and verify the generated output. Spreadsheets are editable, so charts and numbers can be adjusted post-generation.

### Step 5: Generate Interactive HTML Simulations and Games

1. Write a prompt that describes the simulation or game, lists the required features, and explicitly states "Put everything in a standalone HTML file" and "Make sure it loads efficiently in a regular browser."
2. Include adjustable parameters for any tunable inputs: reflectivity, roughness, and clear coat for materials simulations; seed and biome toggles for terrain maps.
3. Press **Generate**, then expand the result to full width in a new tab.
4. Interact with the output to verify all specified controls and behaviors work correctly.
5. Use follow-up prompts to fix issues (e.g., "make the spheres reflect each other," "allow me to change the time of day and make sure the lighting actually changes").

### Step 6: Use GLM5 Locally or via Application Programming Interface (API)

1. For local deployment, go to the GLM5 Hugging Face page or official GitHub repository. Note the full model is 1.5 TB in size and is intended for enterprises with strict data security and privacy requirements, not consumer hardware.
2. To use GLM5 via API, subscribe through Z.AI. The cheapest plan is $27 per quarter ($9 per month).
3. In coding agents such as Claude Code, switch the underlying model to GLM5 via API to benefit from its coding accuracy and cost efficiency during development.

## Examples

### Example 1: Educational Course Generator

**Prompt (Agent Mode):** "Make a fun educational course on chemistry for kids consisting of sequential lessons. Include real images and interactive visual exercises."

**Result:** GLM5 produces a fully structured interactive web course with sequential lessons, lesson locking, quizzes, drag-and-drop atom builders, element matching games, molecule construction exercises, and progress tracking—all from one prompt.

### Example 2: Mobile OS Concept Design

**Prompt (Agent Mode):** "I want to develop an OS for mobile that's even better than Android or iOS. Include eight apps on the home screen. Explain what you designed, how things work, and your rationale behind it."

**Result:** GLM5 generates a fully designed mobile interface with eight named apps (Pulse, Canvas, Nexus, Flow, Vault, Horizon, Mirror, Bridge), each with a working UI mockup and written design rationale explaining why each app improves on existing platform weaknesses.

### Example 3: Interactive Stock Chart Visualizer

**Prompt (Regular Chat):** "Create a stock price chart visualizer with data from the attached file. Allow me to switch between line chart and candlestick views. Allow me to select a past date and replay it. Add moving average, RSI, and other indicators."

**Result:** GLM5 produces a standalone interactive chart viewer with line and candlestick views, date-range replay controls, 5/10/20/60-day moving averages, exponential moving average, Bollinger Bands, and RSI overlay.

### Example 4: 2D Platformer Game

**Prompt (Agent or Regular Chat):** "Create a 2D platformer game similar to Super Mario. Make it look amazing. Put everything in a standalone HTML file. Use publicly available assets, models, and effects for the game."

**Result:** GLM5 generates a complete playable platformer with parallax backgrounds, dynamic sky gradients, procedurally drawn characters, particle effects, smooth physics, two enemy types (bouncing slimes and flying bats), stomping mechanics, coin collection, a lives system, and infinite procedurally generated levels—all in one prompt.

## Best Practices

- ✅ Use Agent mode when you need more than one file, page, or coordinated output; use regular Chat for single-file or single-output tasks.
- ✅ Always explicitly specify the output format in your prompt (HTML, Excel, CSV, standalone file, editable spreadsheet).
- ✅ Use follow-up prompts to correct specific issues in generated output rather than starting over.
- ✅ Take advantage of multimodal input by uploading PDFs, CSVs, and images to get richer, more structured results.
- ✅ Verify factual outputs (medical, legal, financial) independently—GLM5 is not a licensed professional tool and can produce inaccurate information.
- ✅ Use GLM5 in coding agents such as Claude Code via API to benefit from its coding accuracy; the Z.AI API subscription costs $9 per month ($27 per quarter).

## Keep In Mind

- GLM5's full model is 1.5 TB in size. Local deployment is intended for enterprises with strict data security and privacy requirements. Consumer hardware cannot run the full model, as noted in the video.
- GLM5 has a 200,000-token context window (150,000 words). This is smaller than competing models like Gemini 3 Pro, which has a 1-million-token context window.
- GLM5 is a Mixture of Experts (MoE) model with 744 billion total parameters, but only 40 billion are active per inference, making it efficient despite its size.
- When using Agent mode, generated outputs may default to Chinese even when the prompt is in English, as observed in the video demo. Use a follow-up prompt to request outputs in your preferred language.
- Agent mode creates outputs in a sandbox environment. Regular Chat mode generates one output at a time.
- GLM5's API is rolling out to coding plan subscribers before becoming widely available across all coding agents.

## Security & Safety Notes

- GLM5 is open-source and can be run locally, which keeps your data private by preventing prompts and uploaded files from being transmitted to third-party servers. Note that local privacy depends on the deployment environment.
- Closed proprietary models (GPT, Claude, etc.) send chat data to their servers, giving them potential access to your information. If you are working with sensitive or proprietary information, prefer local deployment of GLM5.
- When using the free Z.AI platform or API, review Z.AI's published terms of service and data handling policies for any sensitive use cases.
- Always independently verify AI-generated medical, legal, or financial information before acting on it. GLM5 is not a substitute for licensed professionals.

## Glossary

- **Agent mode**: A GLM5 mode that automatically generates a to-do list, plans the work, and executes it step by step in a sandbox environment to produce multi-file or multi-page outputs from a single prompt.
- **Artificial Analysis**: A third-party leaderboard that ranks LLMs based on performance benchmarks.
- **Hallucination rate**: A metric measuring how often a model produces incorrect or unsupported information on a benchmark; lower scores indicate fewer hallucinations.
- **Regular Chat**: A GLM5 mode that generates one output at a time, suitable for single-step Q&A, single-file code generation, or single-output analysis tasks.
- **Sandbox environment**: An isolated execution environment where the agent builds, tests, and refines multi-file outputs before delivering the final result.

## Common Pitfalls

- **Problem:** Generated 3D scenes from images default to nighttime even when the prompt describes a daytime scene, as occurred when the model generated a cherry blossom and pagoda scene that defaulted to nighttime instead of daytime.
  **Solution:** Add a follow-up prompt explicitly requesting the correct time of day and that lighting updates dynamically (e.g., "allow me to change the time of day and make sure the lighting actually works").

- **Problem:** Generated code or simulations do not reflect all requested interactions (e.g., spheres that do not reflect each other, charts that do not respond to controls).
  **Solution:** Test the output interactively immediately after generation. Use a specific follow-up prompt naming the missing behavior to fix it.

- **Problem:** Agent mode outputs are in the wrong language (defaults to Chinese despite English prompts).
  **Solution:** Add a follow-up prompt explicitly requesting all text content be in English or your preferred language.

- **Problem:** Financial or medical analysis outputs contain errors or unsupported claims.
  **Solution:** Cross-check all figures, drug names, and conclusions against primary sources. Treat AI output as a draft or research starting point, not a finalized report.

- **Problem:** Attempting to download and run the full GLM5 model on consumer hardware.
  **Solution:** The full model is 1.5 TB. Consumer hardware cannot run it. Use the Z.AI platform or API, or run it locally for enterprises with data security requirements.
