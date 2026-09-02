# OpenCode + Gemma 4 31b = Full Apps (100% FREE)

## Overview

This AI teaching demonstrates how to use Google's Gemma 4 31B open source model through OpenRouter and OpenCode to build websites and applications. The model is available for free on OpenRouter, and the video creator reports building a Next.js landing page with semantic HTML, responsive CSS, structured data for SEO (Search Engine Optimization), and mobile-first layout. The model also can be run locally via Ollama.

## When to Follow These AI Teachings

- When you want to build websites or apps without paying for premium AI coding assistants
- When you have OpenCode installed and want to use a free open-source model
- When you need websites with semantic HTML, responsive CSS, structured data for SEO (Search Engine Optimization), and mobile-first layout
- When you want to test if a free 31B parameter model can replace paid coding assistants
- When you have a computer with sufficient RAM to run models locally via Ollama

## Steps

### Step 1: Update OpenCode to the Latest Version

Ensure you are on the latest version of OpenCode before proceeding. Open your terminal and run `opencode --version` to verify your OpenCode installation is up to date.

### Step 2: Refresh Available Models

Run the following command to refresh the model list in OpenCode:

```bash
OpenCode Models --refresh
```

This ensures you can see the latest available models including the free Gemma 4 31B option.

### Step 3: Select the Gemma 4 31B Free Model

Search for and select the model named `Open Router Gemma 4 31B IT free`. This is the model you need to use the entire coding system completely for free with zero cost.

### Step 4: Run Your Initial Coding Prompt

Use a concrete prompt to test the model. For example: "Build a Next.js 14 landing page with TypeScript, Tailwind CSS, a hero section, three feature cards, a footer, Open Graph meta tags, and mobile-responsive layout." The model will ask for clarification if it cannot find an existing project context. If it asks for help, respond with "Start from scratch" and add "Don't use superpowers" if you want to test the base model without additional skills.

### Step 5: Iterate and Refine the Output

After the initial build, use follow-up prompts to improve the result. Examples:
- "Needs a header and a footer"
- "Add a header, footer, navigation bar, about section, and contact form, then expand each feature card with use-case descriptions and supporting metrics"
- "Add a pricing table, testimonial section, and FAQ accordion with at least five questions and detailed answers"

Continue prompting until the build includes the desired sections and features. The video creator describes prompting the model two or three times to add detail, stating: "If you have to prompt it two times, three times, it's free. Like, what do we care about bloody prompting it a couple of times, guys?"

## Examples

### Example 1: Building a Next.js Website From Scratch

The video creator used a standard Next.js community prompt. The model initially asked where the Next.js project was, then after the video creator told it to start from scratch, the video creator built a Next.js landing page in 10 to 15 minutes using the model. The video creator describes the technical build as "perfect" and reports "not a single dead link anywhere."

### Example 2: Adding Detail and Polish

After the initial build, the video creator used simple prompts like "Needs a header and a footer" and "Add more detail" to improve the site. The model responded with clean implementations of headers, footers, and expanded content.

### Example 3: Local Deployment via Ollama

If you have a computer with at least 128GB of RAM, install Ollama, download the Gemma 4 31B model, and connect OpenCode to Ollama to run the model completely offline and for free.

## Best Practices

- ✅ Update OpenCode and refresh models before selecting Gemma 4 31B
- ✅ Use "Start from scratch" when the model gets confused about project context
- ✅ Use follow-up prompts to refine and add detail to builds; the video creator describes prompting the model two or three times to add sections and detail
- ✅ Test with concrete prompts (for example, a landing page, a form, or a dashboard component) and verify the output includes semantic HTML, responsive breakpoints, SEO meta tags, and clean code structure before using the model for production builds
- ✅ Use a computer with at least 128GB RAM if running locally via Ollama
- ❌ Don't expect the model to build everything from A to Z in a single prompt without any follow-up
- ❌ Don't assume content will be translated in multilingual builds without explicit prompting
- ❌ Don't run the 31B parameter version on computers with less than 128GB RAM

## Keep In Mind

- Gemma 4 31B has a 262,000-token context length
- The model will stop after the initial build and require follow-up prompts to continue improving
- The video creator reports building a Next.js landing page in 10 to 15 minutes using the free Open Router version of Gemma 4 31B
- The 31B parameter version requires at least 128GB of memory and is not suitable for computers with less than 128GB RAM
- RTX 4090, 3090, or 3060 GPUs (Graphics Processing Units) are sufficient to run the 31B model locally via Ollama
- The model generates output with consistent indentation and semantic HTML class names

## Security & Safety Notes

- Gemma 4 31B uses the Apache 2.0 license, making it fully open source
- Running the model locally via Ollama keeps your code and data private
- Using the free Open Router version means your requests pass through OpenRouter's servers
- No API keys or payment information are required for the free Open Router version

## Common Pitfalls

- **Problem:** Model asks for help when it cannot find an existing project
  **Solution:** Tell it to "Start from scratch" and proceed with the build
- **Problem:** Incomplete translations in multilingual websites
  **Solution:** Prompt specifically to translate remaining content, as the model only translates portions of the site
- **Problem:** Model stops after initial build without adding further detail
  **Solution:** Use explicit follow-up prompts such as "Keep making this more detailed" or "Add more features"
- **Problem:** Not enough RAM to run the model locally
  **Solution:** Use the free Open Router version instead, or upgrade to a system with at least 128GB RAM for local Ollama deployment
- **Problem:** Model is not available in Antigravity (an AI model platform)
  **Solution:** Use OpenCode with OpenRouter directly, as the model is available there for free
