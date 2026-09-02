# You've Been Using AI the Hard Way (Use This Instead)

## Overview

This AI teaching instructs you to abandon browser-based AI interfaces and switch to terminal-native AI tools including Gemini CLI, Claude Code, OpenCode, and Codex. The core benefit is owning your project context locally as files, delegating tasks to specialized agents with fresh context windows, and orchestrating AI instances simultaneously without copy-pasting between browser tabs.

## When to Follow These AI Teachings

- When your browser-based AI chats exceed context limits and you lose track of project state across 20 chat windows
- When you need AI to read, write, and execute code or scripts on your local machine instead of copying outputs back and forth
- When you want to delegate tasks such as home lab research, code review, session summarization, or critique to specialized agents without bloating your main conversation context
- When you need to switch between different AI models or providers within the same project workflow
- When you want persistent project memory that survives new chat sessions through markdown context files

## Steps

### Step 1: Install a Terminal AI Tool

Choose and install one of the three terminal AI tools. Gemini CLI supports Gemini 2.5 Pro. Claude Code supports Claude. OpenCode is open source and supports local models like Llama 3.2 via Ollama or cloud subscriptions.

**Gemini CLI:**
```bash
npm install -g @google/gemini-cli
```

**Claude Code:**
```bash
npm install -g @anthropic-ai/claude-code
```

**OpenCode (open source, supports local models):**
```bash
npm install -g opencode
```

Run with `sudo` if installation fails with permission errors on Mac or Linux. After installation, restart your terminal or source your shell config file by running `source ~/.bashrc`, `source ~/.zshrc`, or `source ~/.config/fish/config.fish` depending on your shell.

### Step 2: Create a Project Directory and Initialize Context

Create a dedicated project folder and open the terminal AI tool from inside it.

```bash
mkdir my-project
cd my-project
gemini   # or `claude` or `opencode`
```

Log in with your Google account for Gemini CLI, Anthropic account for Claude Code, or GitHub account for OpenCode when prompted. Grant the tool permission to access the current folder by typing `y` or `yes` when the terminal asks for filesystem access.

### Step 3: Create a Persistent Context File

Create a markdown file named `GEMINI.md`, `CLAUDE.md`, or `AGENTS.md` depending on the tool. This file acts as persistent project memory.

From within the terminal AI tool, run `/init` to scan your current directory and generate a context file automatically. This creates `GEMINI.md` for Gemini CLI, `CLAUDE.md` for Claude Code, or `AGENTS.md` for OpenCode based on your project contents. If the tool does not support `/init`, create the file manually and write your project goals, current status, key decisions, and relevant documents. Every new session launched in this directory will load this file as context automatically.

### Step 4: Verify Context Persists Across Sessions

Open a fresh terminal session in the same directory and launch the AI tool again. Confirm the tool displays the context file name or its contents in the initial session output. Ask a question that references earlier project decisions without re-explaining context. The tool should respond correctly based on the context file.

### Step 5: Create Specialized Agents for Task Delegation

In Claude Code, create a project-specific agent to delegate tasks to a specialized agent and preserve your main conversation context. Project-scoped agents are available only in the directory where they are created and do not clutter your global agent list.

Run:
```
/agents
```

Select "Create new agent." Choose "Project" scope so the agent is available only in the current directory. Give the agent a specific role such as "home lab research expert" or "code reviewer." Grant only the tools the agent needs: Read, Write, Edit, Bash, and Glob for file operations; WebSearch for research; or Grep for code search. Save the agent by confirming the name and permissions.

To invoke the agent from your main conversation, use the `@` symbol followed by the agent name. Claude will delegate the task to a fresh agent instance with its own context window, keeping your main conversation free of delegated task outputs.

### Step 6: Run Multiple Agents Simultaneously

Create additional agents for different tasks. Invoke them in the same prompt by referencing each with `@agent-name`.

For example, run a home lab research agent and a separate general research agent at the same time. Each agent operates independently with its own context and can write files to the shared project directory.

Monitor running agents by pressing `Ctrl+O`. You can interrupt with `Ctrl+C` and resume the conversation later with `claude -r --dangerously-skip-permissions` if you need to restore a previous session after closing the terminal or if the agent crashed mid-task.

### Step 7: Use Output Styles to Control AI Behavior

In Claude Code, create a custom output style that changes how the AI responds across your entire project.

Run:
```
/output-style
```

Select "New" and describe the persona or behavior you want (for example, "You are a home lab expert designed to help me design a home lab that balances performance, cost, and power efficiency"). Save the style. The AI will adopt this behavior in every new session for this project.

Toggle between output styles with `Shift+Tab` or switch to Planning Mode to have Claude generate a full plan, await your approval, then Claude executes the plan.

### Step 8: Orchestrate Multiple Terminal AI Tools Together

Run Gemini CLI, Claude Code, and OpenCode in the same project directory. Copy the same project goals, current status, key decisions, and relevant documents into `GEMINI.md`, `CLAUDE.md`, and `AGENTS.md` so all tools share identical context. Have each tool write its output to separate files in the shared directory. No copy-pasting is needed because all tools read and write the same local files.

### Step 9: Automate with Headless Mode

Run terminal AI tools without the interactive TUI when you want to execute a single prompt from a shell script, cron job, or CI/CD pipeline. Headless mode is also useful for scheduled tasks such as nightly report generation, batch file processing, or automated validation checks that run without manual interaction.

```bash
gemini -p "Your prompt here"
```

Use headless mode inside custom agents or scripts when you want non-interactive execution. Combine headless calls with file-based context so each run is aware of project state.

### Step 10: Commit Project State to Git for History and Recovery

Treat your AI project folder like code. Stage changes, commit with descriptive messages such as "Add home lab research notes and NAS recommendations," and push to a remote repository such as GitHub. This preserves a history of decisions, generated files, and context changes. If something breaks or you need to revert a decision, you can restore any previous state from git history by checking out the relevant commit.

### Step 11: Use a Session-Closing Agent to Sync State Daily

Create a personal agent (available across all projects) named "session-closer." Instruct it to perform these exact steps:
1. Read all files modified during the current session.
2. Write a summary to `session-summaries/YYYY-MM-DD.md` listing what was discussed, decided, and completed.
3. Update `GEMINI.md`, `CLAUDE.md`, and `AGENTS.md` with the latest project status, key decisions, and next steps. Copy the same content into all three files.
4. Run `git add .`, `git commit -m "Session sync: YYYY-MM-DD"`, and `git push` to save the state.

Run this agent at the close of each work session. The next day, open a fresh terminal session, launch any AI tool, and ask where the project stands. The context files and git history will restore your state immediately.

### Step 12: Deploy a Brutal Critic Agent for Unbiased Feedback

Create an agent named "brutal-critic" whose only job is to critique your work without the bias of your current conversation. Write explicit instructions such as: "You are a security auditor reviewing code for vulnerabilities, performance problems, and unclear logic. Do not sugarcoat feedback. Reference these project standards: your team's coding standards and style guide, target audience: the intended end users of the software."

When you want feedback, invoke the brutal critic agent on your current draft. It will review the file with fresh context and provide direct, unfiltered criticism. Use this feedback to improve your work before finalizing it.

## Examples

### Example 1: Video Scriptwriting Workflow

Create a project folder named `video-script-project`. Write your outline in `outline.md` with timestamps, key points, and sources. Create `GEMINI.md` with your channel name, audience demographics (for example, "software engineers aged 25-40"), tone ("conversational but technical"), and current segment goals. Open three terminal windows: one running `claude`, one running `gemini`, and one running `codex`.

Ask Claude to write a hook and save it to `authority-hook.md`. Ask Gemini to write a discovery angle hook and save it to `discovery-hook.md`. Ask Codex to review both hooks and select the stronger option. All three tools read and write the same local files with no copy-pasting.

### Example 2: Home Lab Research Agent

Create a project folder named `home-lab`. Create a project-local Claude agent named "home-lab-guru" using `/agents` with Project scope. Give it the research task: "Find the best 4-bay NAS under $500 for a home lab running Proxmox and TrueNAS. Compare Synology, QNAP, and custom build options. Write results to `nas-research/nas-recommendations.md` with a comparison table." While that agent runs, invoke a second agent named "local-restaurant-finder" to research the best pizza place within 2 miles of your zip code. Both agents run simultaneously in the same terminal. Monitor progress with `Ctrl+O` to see which agent is active. Both write to separate files in your project folder.

### Example 3: Persistent Project Context for Long-Form Content

Create a `gemini.md` file in your video project folder with the full video structure, key decisions made so far, target audience, tone guidelines, and the exact timestamp where you stopped writing. Over days, work on the script in brief 15-30 minute sessions. Each time you launch Gemini in that folder, it loads `gemini.md` and knows exactly where you left off. No re-explanation needed.

At the end of each session, run your session-closing agent to append new decisions to `gemini.md`, copy the same updated content into `claude.md` and `AGENTS.md`, and commit to git. The next day, open any terminal AI tool and immediately resume work without context loss.

### Example 4: Switching Models Mid-Project with OpenCode

Install OpenCode with `npm install -g opencode`. Configure it with a local Llama 3.2 7B model via Ollama for offline work by running `ollama run llama3.2` and then selecting the model in OpenCode's model picker. Use OpenCode with local models when you are away from internet. When you need a more powerful model, log in with your Claude Pro subscription inside OpenCode by running `/login anthropic`, then switch to `claude-sonnet-4-5` using `/model claude-sonnet-4-5`. All your project files and context remain in the same local folder regardless of which model you use.

## Best Practices

- ✅ Create a dedicated project directory for every project and launch the AI tool from inside it.
- ✅ Keep one shared context file per tool (`GEMINI.md`, `CLAUDE.md`, `AGENTS.md`) and keep them synchronized.
- ✅ Use project-scoped agents for specialized tasks to keep your main conversation context clean.
- ✅ Commit your project folder to git at the end of every session to preserve history and enable rollback.
- ✅ Design at least one brutal critic agent to get unbiased feedback on your work.
- ✅ Use output styles to control AI behavior consistently across sessions.
- ✅ Run terminal AI tools in the same directory to leverage different models for different roles.
- ✅ Use headless mode (`gemini -p`, `claude -p`) for automation and scripted workflows.

## Keep In Mind

- Terminal AI tools expose your context window usage directly. Browser tools hide this from you.
- Context files are plain markdown on your hard drive. You own them, you control them, and they are not locked to any single vendor.
- Agents run as separate instances with fresh context windows. They do not inherit the bias or history of your main conversation.
- Output styles in Claude Code are project-specific or global. You can switch between them with `Shift+Tab`.
- OpenCode supports local models, cloud subscriptions, and model switching mid-session in the same project directory.
- Planning Mode in Claude Code generates a full plan and waits for your approval before executing.

## Security & Safety Notes

- Terminal AI tools have direct read and write access to your local filesystem. Only grant access to folders you trust the tool to modify.
- Use `--dangerously-skip-permissions` only when you fully understand what the AI will execute on your machine.
- If you share your computer with others, lock your AI authentication sessions and avoid leaving terminal AI tools running unattended with broad filesystem access.
- Remote employees or remote machines running terminal AI tools over traditional VPNs can inadvertently give the AI access to the entire internal network. Prefer zero-trust remote access solutions that restrict each device to only the resources it needs.
- Local models in OpenCode keep your data on your machine. Cloud models transmit prompts and context to the provider. Choose based on your data sensitivity requirements.

## Common Pitfalls

- **Problem:** Context files become outdated and out of sync across tools.
  **Solution:** Run a dedicated session-closing agent at the end of every work session to regenerate and sync all context files before committing to git.

- **Problem:** Main conversation context becomes bloated after long sessions.
  **Solution:** Use project-scoped agents to delegate research, writing, and review tasks. Each agent gets a fresh 200K-token context window.

- **Problem:** Forgetting which model is active and accidentally using the wrong one.
  **Solution:** In OpenCode, use `/model` to verify your active model before starting important work.

- **Problem:** Browser habits persist and you forget to leverage local files.
  **Solution:** Always ask the terminal AI to write results to files in your project directory instead of only showing them in chat. Make file creation part of every prompt.

- **Problem:** Agents perform unwanted filesystem changes because permissions were too broad.
  **Solution:** Review agent tool access carefully when creating agents. Grant only the permissions the agent needs for its specific task.

## Glossary

- **Agent mode**: A mode in ChatGPT Atlas where the AI watches entire videos and performs tasks like finding specific moments or answering detailed questions about video content.


(End of file - total 198 lines)
