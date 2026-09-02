# New Open Source AI Matching Claude Fable 5 and GPT 5.6 on Humanity's Last Exam

## Overview

GLM 5.3 is an open-source AI model from ZAI that matches Claude Fable 5 and GPT 5.6 on tasks for most instances. It is designed for agentic coding and long-horizon autonomous tasks—tasks that require extended reasoning and tool use over minutes or hours, such as building a realistic animated V8 engine in Blender (demonstrated for roughly one hour) or creating a browser-based Windows OS replica (demonstrated for 22 minutes). It operates through a coding harness such as Zcode, where it can reason through multi-step problems, autonomously call tools, and iterate until a goal is achieved. This AI Teaching synthesizes the demonstrated behaviors from the GLM 5.3 release transcript into actionable guidance for leveraging frontier-class open-source models for complex engineering, creative, and security workflows.

## When to Follow These AI Teachings

- When you need to build complex multi-file software projects entirely through AI-generated code
- When you want an AI to autonomously operate external tools such as Blender, Digital Audio Workstations (DAWs), or web browsers
- When you need deep research, financial analysis, or security auditing on open-source repositories
- When you are comparing open-source models that match Claude Fable 5 and GPT 5.6 for most instances, and need to understand their capabilities and limitations

## Steps

### Step 1: Access GLM 5.3 Through a Coding Harness

Subscribe to the GLM coding plan. After subscribing, access GLM 5.3 exclusively through Zcode or a compatible coding harness. It is not available via direct API or online chat at launch. After subscription, open Zcode, select GLM 5.3 from the model list, and begin working inside the harness.

### Step 2: Configure the Thinking Level for Complex Tasks

For long-horizon tasks such as building full applications, 3D models, or games, set the thinking level to max before pressing run. This enables the model's highest reasoning effort for these tasks. Lower thinking levels are suitable for tasks like writing emails, summarizing, research, and data analysis, but max is required for multi-step autonomous builds. Demonstrated long-horizon tasks ranged from 11 minutes for deep research to one hour for building a realistic animated V8 engine in Blender, including a 22-minute browser-based Windows OS replica and a 53-minute music composition.

### Step 3: Structure Prompts for Autonomous Agentic Work

Write prompts that give the model a clear end goal with specific deliverable requirements. Include the tools or platforms the model should use, the expected output format, and any platform constraints. Example structure: state the project, list required apps or features, specify efficiency or compatibility constraints, and ask the model to verify the result itself.

### Step 4: Provide Explicit Correction Instructions When Outputs Are Wrong

When the model produces incorrect artifacts, write follow-up prompts that identify the specific problem and state exactly what must be fixed. For example, if a 3D model has parts floating instead of assembled, write a prompt that names the misplaced components and instructs the model to reassemble them properly. Continue iterating with explicit corrections.

### Step 5: Use the Model for Multi-Tool Autonomous Workflows

The model can autonomously discover and operate external applications. Instruct it to use specific tools such as Blender MCP (Model Context Protocol), Digital Audio Workstations (DAWs), or browser automation extensions. If a task requires an authenticated session, provide the address of the Playwright Chrome extension or local session proxy and explicitly tell the model to use the existing logged-in session rather than re-authenticating.

### Step 6: Run Security Scans With Open Vone

Use ZAI's free Hugging Face space called Open Vone to scan any public GitHub repository for security vulnerabilities. Paste the GitHub link into Open Vone, let the system queue the repository, and receive an encrypted report. Only verified project owners receive the full vulnerability details. The public sees only summary counts, not exploit details.

## Examples

### Example 1: Build a Browser-Based Operating System

Prompt: "Create a browser-friendly replica of Windows 11. Include common apps and programs like Microsoft Office, Microsoft Store, Photos, File Explorer, Media Player, Discord, Slack, and Spotify. Make sure these programs work. Make sure it runs efficiently on a regular web browser. Set thinking level to max."

The model spent 22 minutes building core OS components, then spawned separate sub-agents to build individual apps. It self-tested the result, identified bugs, and auto-fixed them before delivering a working Windows replica with functional settings, Office apps, Paint, and Slack interface.

### Example 2: Create a Realistic Animated V8 Engine in Blender

Prompt 1: "Using Blender MCP at this address, make a realistic animated V8 engine."
Prompt 2: "Make sure it looks as detailed and realistic as possible. Make sure the components are in the right places."
Prompt 3: "There are bolts and other parts scattered around the engine. Make sure these parts are assembled properly within the engine instead of floating around it."

The model autonomously controlled Blender through MCP and created components including pistons, springs, and bolts, then wired up animations. Final session duration was one hour.

### Example 3: Generate a Financial Analysis Presentation Video

Prompt: "From the recent earnings reports of Tencent, Alibaba, and BYD, create a professional presentation video that thoroughly compares their financials and future outlook. Include a voice over using Gemini TTS (Text-to-Speech). It should be a motion graphics video, 16:9, black background, one minute long. Include graphs, charts, and data visualizations. Use this piece as the background music. Here is an example of how to use Gemini TTS: the API documentation on how to use the voiceover. Here is my API key, which I'm going to delete before I publish the video."

The model autonomously selected Hyperframes for motion graphics, analyzed financials, generated voiceover, and produced a rendered video. If the text styling was incorrect (for example, all lowercase instead of title case for names and acronyms), a follow-up prompt corrected it without manual editing.

### Example 4: Scan an Open-Source Repository for Vulnerabilities

Use Open Vone by pasting a GitHub repository link such as Hermes, LangChain, or LlamaCPP. The system returns a vulnerability count and severity breakdown. For example, a scan of Hermes returned 21 vulnerabilities. Details remain encrypted and are shared only with verified project owners.

## Best Practices

- ✅ Always set thinking level to max for complex builds
- ✅ Break complex tasks into a primary prompt plus targeted follow-up corrections
- ✅ Provide local tool addresses or extension references when the model needs to control external software
- ✅ Let the model verify its own output by asking it to test, screenshot, or load the result in a browser
- ✅ Use the Open Vone workflow for periodic security audits of open-source dependencies
- ✅ Delete API keys from any prompt text before publishing or sharing the conversation
- ✅ Review generated assets for subtle errors such as incorrect icons, misplaced geometry, or missing features, then prompt for corrections

## Keep In Mind

- GLM 5.3 does not have native vision capabilities, so image analysis requires autonomous tool calls to external Python tools or vision models. Expect image tasks to be slower and less reliable than text tasks.
- The model is currently available only through Zcode or a coding harness. Direct API access and online chat access are not yet available. ZAI has stated both will be released, but no release date has been confirmed.
- Open-source weights release is scheduled for two weeks after launch once safety evaluation and hardening are complete. Model size is 1.5 TB full, with an FB8 (quantization format) version at 756 GB and a Q1 GGUF (1-bit quantization) version at 217 GB.
- Demonstrated long-horizon tasks ranged from 11 minutes for deep research to one hour for building a realistic animated V8 engine in Blender, including a 22-minute browser-based Windows OS replica and a 53-minute music composition. Plan sessions accordingly and save intermediate outputs.

## Security & Safety Notes

- The Open Vone vulnerability scanner encrypts all vulnerability details. Only verified repository owners receive the full report. The public sees only aggregate counts.
- When using API keys in prompts, remove the key from any published or shared transcript. The model does not automatically redact credentials from prompt history.
- GLM 5.3 autonomously controlling external tools such as browsers or Blender has access to the full capabilities of those tools. Restrict tool access to environments where unintended actions will not cause data loss or security issues.
- Review all AI-generated code, 3D models, and media before deploying them to production. Autonomous agents can introduce functional bugs, licensing issues, or security flaws even when the final output appears correct.

## Common Pitfalls

- **Problem:** Model outputs wrong image analysis or identifies incorrect objects, such as identifying a cat in an image that contained no cat, or misidentifying tumor types in brain scan images.
  **Solution:** Recognize that GLM 5.3 lacks native vision. For image tasks, provide explicit instructions to use a specific vision tool and verify results. Expect hallucinations on complex image analysis.

- **Problem:** Model cannot access authenticated websites such as Sketchfab or Mixamo.
  **Solution:** Provide the address of the Playwright Chrome extension or local session proxy, and explicitly instruct the model to use the existing logged-in Chrome session rather than opening a new browser instance.

- **Problem:** Animations or 3D assets are misaligned, detached, or floating, such as a character not holding a sword correctly, bolts and engine parts scattered and floating around an engine instead of assembled, or a character submerged halfway into the ground.
  **Solution:** Submit a follow-up prompt that names the specific broken asset or component and states the exact correction needed. Do not rely on the model to self-correct without explicit guidance.

- **Problem:** Long-horizon task fails partway through due to context or time limits.
  **Solution:** Break the task into sequential phases. Build the core foundation first, validate it, then prompt for extensions. Do not attempt to build a full 3D game or operating system in a single uninterrupted session.

- **Problem:** Generated video text is entirely lowercase or styled incorrectly.
  **Solution:** Issue a targeted follow-up prompt specifying the exact text formatting requirements, such as uppercase first letters for names and acronyms. Do not re-run the entire generation from scratch.
