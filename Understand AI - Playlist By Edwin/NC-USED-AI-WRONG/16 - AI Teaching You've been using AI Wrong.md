# AI Teaching: You've been using AI Wrong

## Overview

This AI teaching demonstrates how to use Fabric, an open-source command-line tool that eliminates copy-paste between chat interfaces and your terminal by using reusable, community-curated prompt patterns called "patterns" collected by Daniel Meisler and Fabric contributors. Instead of manually copying content into chat interfaces, Fabric lets you pipe text directly into curated AI prompts from your terminal, stream results, chain patterns together, and save outputs to Obsidian. The core philosophy is that AI should augment human thinking rather than replace it, and the best way to achieve that is by building a personal library of patterns that solve specific problems you encounter regularly.

## When to Follow These AI Teachings

- When you want to extract insights from YouTube videos, podcasts, or articles without watching or reading them in full
- When you need to process text data through AI from the command line
- When you want to chain at least two AI operations together in a single workflow
- When you want to create and maintain your own reusable AI prompts tailored to your needs
- When you want to integrate AI processing into scripts, notes, or knowledge management systems like Obsidian
- When you want to use local LLMs instead of cloud-based AI services

## Steps

### Step 1: Install Fabric

Run the following commands in your terminal to clone the Fabric repository and install it:

```bash
# Clone the Fabric project
git clone https://github.com/danielmiessler/fabric.git
cd fabric

# Install PIP X (required for installation)
# On Mac with Homebrew:
brew install pipx
# On Linux or WSL:
sudo apt install pipx

# Install Fabric
pipx install .

# Ensure the path is set correctly
pipx ensurepath
```

### Step 2: Refresh Your Shell

After installation, refresh your shell so Fabric is available in your PATH:

```bash
# On Linux:
source ~/.bashrc

# On Mac with ZSH:
source ~/.zshrc
```

### Step 3: Run Fabric Setup

Run the setup command to configure your API keys:

```bash
fabric --setup
```

You will be prompted to enter:
- OpenAI API key (for GPT-4 and other OpenAI models)
- Anthropic API key (for Claude models)
- YouTube API key (free to set up via Google Cloud Console)

### Step 4: Verify Installation

Check that Fabric is working by listing available patterns:

```bash
fabric --list
```

### Step 5: Extract Wisdom from a YouTube Video

Use the built-in `yt-transcript` tool to grab a YouTube transcript and pipe it into Fabric with a pattern:

```bash
yt-transcript "https://www.youtube.com/watch?v=dQw4w9WgXcQ" | fabric -s -p extract_wisdom
```

Common patterns include:
- `extract_wisdom` - Extract ideas, insights, and quotes from content
- `summarize` - Create a concise summary
- `right_essay` - Summarize content, then transform the summary into an essay
- `analyze_claims` - Analyze claims in content
- `label_and_rate` - Assign a quality tier and consumption recommendation

The `-s` flag streams the output in real time, and `-p` specifies which pattern to use.

### Step 6: Use Local or Remote LLM Models

List available models:

```bash
fabric --list-models
```

Use a local model:

```bash
echo "Your input text here" | fabric -m llama3:latest -p extract_wisdom
```

Use a remote model on another server:

```bash
echo "Your input text here" | fabric -m llama3-70b --remote-llama-server Terry -p extract_wisdom
```

Change your default model:

```bash
fabric --change-default-model llama3:latest
```

### Step 7: Chain Patterns Together with Stitching

Pipe the output of one Fabric command into another to chain patterns:

```bash
# Example: Summarize an article, then turn the summary into an essay
echo "the full article text about the YouTuber Poppy" | fabric -p summarize | fabric -p right_essay
```

### Step 8: Create a Custom Pattern

Create your own reusable pattern by following these steps:

1. Create a directory for your custom patterns to keep them separate from built-in patterns:

```bash
mkdir -p ~/.config/fabric/my-patterns
cd ~/.config/fabric/my-patterns
```

2. Create a new directory for your pattern:

```bash
mkdir sermon-sensei
cd sermon-sensei
```

3. Create a `system.md` file that contains the prompt instructions:

```bash
nano system.md
# Paste your pattern instructions, then save and exit
```

4. Copy your custom pattern into Fabric's patterns directory:

```bash
cp -r ~/.config/fabric/my-patterns/* ~/.config/fabric/patterns/
```

5. Verify your pattern is available:

```bash
fabric --list
```

### Step 9: Configure a Context File

Create a context file to give Fabric persistent background information about your goals and interests:

```bash
nano ~/.config/fabric/context
```

Add concrete context such as: "I am a software developer focused on Python and DevOps. Extract implementation-ready code snippets and specific tool names with version numbers." Fabric will append this context to every request so outputs align with your goals.

### Step 10: Save Output to Obsidian

Configure the Obsidian save feature by setting the `OBSIDIAN_VAULT` environment variable:

```bash
nano ~/.config/fabric/.env
# Add: OBSIDIAN_VAULT=/path/to/your/obsidian/vault
```

Save Fabric output directly to an Obsidian note:

```bash
echo "Paste the article text here between the quotes" | fabric -p extract_wisdom --save poppy-article-summary
```

## Examples

### Example 1: Extract Wisdom from a YouTube Video

```bash
yt-transcript "https://www.youtube.com/watch?v=dQw4w9WgXcQ" | fabric -s -p extract_wisdom
```

This retrieves the transcript, pipes it into the `extract_wisdom` pattern, and streams the extracted ideas, insights, and quotes back to you.

### Example 2: Summarize and Essay-ize a Long Article

```bash
echo "Paste the full article text between the quotes" | fabric -p summarize | fabric -p right_essay
```

This first summarizes the article, then transforms that summary into a structured essay.

### Example 3: Create and Use a Custom Sermon Pattern

```bash
# Create the pattern
mkdir -p ~/.config/fabric/my-patterns/sermon-sensei
cd ~/.config/fabric/my-patterns/sermon-sensei
nano system.md
# Write instructions such as: "Extract the main thesis, supporting arguments, and applications from this sermon transcript. Format as markdown with headers."

# Copy to patterns directory
cp -r ~/.config/fabric/my-patterns/* ~/.config/fabric/patterns/

# Use it on a sermon transcript
yt-transcript "https://www.youtube.com/watch?v=dQw4w9WgXcQ" | fabric -s -p sermon-sensei
```

### Example 4: Use a Local LLM to Avoid Cloud Costs

```bash
echo "Give me a list of ice cream flavors and their origin years" | fabric -m llama3:latest -p ai
```

### Example 5: Access a Remote AI Server from Anywhere

```bash
echo "Extract the top 5 key insights from this transcript and format as a numbered list" | fabric -m llama3-70b --remote-llama-server Terry -p extract_wisdom
```

## Best Practices

- ✅ Keep custom patterns in a separate directory like `~/.config/fabric/my-patterns/` so they are not overwritten when you run `fabric --update`
- ✅ Use the `-s` streaming flag to see results in real time for long outputs
- ✅ Start by modifying existing patterns like `extract_wisdom` when learning to write your own
- ✅ Use the `improve_prompt` pattern to refine rough prompt ideas into polished patterns
- ✅ Capture everything as text and transcribe recordings with Whisper AI before piping into Fabric
- ✅ Use Fabric to filter content quality before committing time to deep consumption
- ❌ Do not store API keys in plain text in shared or public repositories
- ❌ Do not let Fabric replace deep thinking for content that should be watched or listened to in full and processed manually
- ❌ Do not skip the context file if you want personalized, goal-aligned results
- ❌ Do not assume all content should be summarized—content that requires slow, deliberate processing where you put in the hard work should be consumed in full without summarization

## Keep In Mind

- Fabric is a framework, not an AI model. It sends text to whichever AI provider you configure, and you pay for API usage on cloud models
- The "World of Text" philosophy means converting all content (notes, recordings, videos) into text so it can be processed by AI anywhere
- Patterns are open source and crowdsourced, curated through community iteration
- Custom patterns remain local unless you voluntarily submit them to the Fabric repository
- The tool is CLI-native by design to reduce friction, but Daniel has expressed interest in adding voice, GUI, and other interfaces
- Using patterns to mimic how you would naturally take notes or process content aligns with how Daniel Meisler designed them to emulate slow, handwritten-style note-taking on videos and podcasts

## Security & Safety Notes

- Store your API keys in `~/.config/fabric/.env`.
- API keys for OpenAI, Anthropic, and YouTube are transmitted to their respective services when using cloud models
- Local LLMs through Ollama or remote Llama servers keep your data on your infrastructure
- Fabric outputs are only as private as the model you choose—cloud models process data on external servers
- The `--remote-llama-server` option requires a network-accessible server; ensure proper firewall and access controls
- Custom patterns and context files are stored locally and are not uploaded unless you choose to contribute them

## Common Pitfalls

- **Problem:** `fabric` command not found after installation
  **Solution:** Run `pipx ensurepath`, then restart your terminal or source your shell rc file (`source ~/.bashrc` or `source ~/.zshrc`)

- **Problem:** Patterns get deleted after running `fabric --update`
  **Solution:** Store custom patterns in a separate directory like `~/.config/fabric/my-patterns/` and copy them into `~/.config/fabric/patterns/` after updates

- **Problem:** API key prompts fail during `fabric --setup`
  **Solution:** Manually create or edit `~/.config/fabric/.env` and add keys in the format `OPENAI_API_KEY=your_key`, `ANTHROPIC_API_KEY=your_key`, `YOUTUBE_API_KEY=your_key`

- **Problem:** Output exceeds practical limits or gets cut off
  **Solution:** Use the `-s` streaming flag to process output incrementally, or split large inputs into smaller chunks before piping into Fabric

- **Problem:** YouTube transcript extraction fails
  **Solution:** Verify the video has captions enabled and that your YouTube API key is valid and has the YouTube Data API v3 enabled in Google Cloud Console

- **Problem:** Clipboard integration fails on Linux or WSL
  **Solution:** Use your display server's clipboard tools or manually echo and pipe text into Fabric

## Glossary

- **Agent mode**: A mode in ChatGPT Atlas where the AI watches entire videos and performs tasks like finding specific moments or answering detailed questions about video content.


(End of file - total 287 lines)
