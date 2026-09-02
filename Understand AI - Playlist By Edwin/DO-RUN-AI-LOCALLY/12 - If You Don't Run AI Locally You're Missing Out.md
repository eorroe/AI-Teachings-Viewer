# If You Don't Run AI Locally You're Missing Out

## Overview

This AI Teaching explains how to download, run, and manage AI large language models entirely on your own computer using Ollama and LM Studio, instead of relying on cloud-based AI services. It covers why local models matter for cost, privacy, offline use, and full control over model versions, then walks through installing Ollama, downloading open-source models, exposing them via a local API server, using LM Studio as a graphical interface, linking Ollama models into LM Studio with GoLLaMA, and understanding quantization so you can run larger models on consumer hardware.

## When to Follow These AI Teachings

- When you want to eliminate API fees, subscriptions, and rate limits from your AI workflow
- When you need AI assistance while offline, such as on a plane or in a location without internet
- When you want data privacy so that what you type does not leave your device
- When you want full ownership over a specific model version that you control and that the provider cannot change remotely
- When you want to power other local tools such as Cursor or custom apps through a local API server
- When you want to fine-tune an open-source model on your own data for a custom use case
- When you want a ChatGPT-like interface for local models without sending data to the cloud

## Steps

### Step 1: Install Ollama

- Open a web browser and navigate to `ollama.com`.
- Click the Download button in the top-right corner of the page.
- Select Windows, macOS, or Linux depending on your operating system.
- Once the installer downloads, double-click it to begin installation.
- On macOS, move the Ollama application into your Applications folder.
- Open Ollama by typing "Ollama" in Spotlight (macOS) or the Start Menu (Windows).
- When Ollama opens, it automatically starts an application programming interface (API) server that other tools can connect to.

### Step 2: Verify the Ollama API Server Is Running

- Open a browser and go to `http://localhost:11434`.
- You should see "Ollama is running" in the top-left corner of the page.
- This confirms the local API server is active and ready to receive requests from apps such as Cursor or custom scripts.

### Step 3: Choose and Download a Model

- Open the Ollama website and click on "Models" in the top-left menu.
- Browse the model library at ollama.com/models. For consumer hardware with integrated or dedicated graphics processing units (GPUs), the speaker recommends models between 4 billion (B) and 40B parameters. The speaker says: "this is the perfect size you need to be looking at between 4 and 40B" for most users without high-end memory.
- For a starting model, a good option is `gpt-oss:20b`, which balances capability and hardware requirements.
- Open a terminal on your computer.
- Type `ollama run gpt-oss:20b` and press Enter. For example: `ollama run gpt-oss:20b`.
- The first run downloads the model and stores it locally in the SafeTensors file format at ~/.ollama/models. A 20B model is 14 GB.
- Download time varies depending on your internet speed. Do not close the terminal until the download completes.

### Step 4: Manage Downloaded Models

- To see every model currently installed on your machine, run `ollama list` in the terminal.
- The output shows the model name, when it was downloaded, and the file size.
- To delete a model you no longer need, run `ollama rm devstral:latest`. For example: `ollama rm devstral:latest`.
- After deleting, run `ollama list` again to confirm it was removed.
- Delete models you no longer need to free disk space. The speaker says: "3 months ago in the open-source AI field is like three decades" and recommends removing models you have not used recently, as open-source models evolve quickly.
- Open-source models evolve quickly. A model older than 3 months is behind the current state of the art. Large models also consume substantial disk space.

### Step 5: Interact With the Model in the Terminal

- Run `ollama run gpt-oss:20b` to open a chat session in the terminal.
- Type your message and press Enter to receive a response.
- To exit the chat, type `/bye` and press Enter.
- Streaming is enabled by default. Tokens appear one by one as the model generates them. To disable streaming, run `ollama run gpt-oss:20b --nowordwrap`.

### Step 6: Connect to the Ollama API Using curl

- Open a terminal and run this curl command:
  ```bash
  curl http://localhost:11434/api/generate -d '{
    "model": "gpt-oss:20b",
    "prompt": "Why is local AI important?",
    "stream": false
  }'
  ```
- The JSON payload includes the model name, your prompt, and streaming settings. Set `"stream": false` to receive the full response at once. Set `"stream": true` to receive tokens incrementally.
- If you receive an error saying the model is not found, run `ollama list` to confirm the exact model name locally and use that name in your request.
- Once configured correctly, the API returns a JSON response containing the model's answer.
- This confirms the model is running entirely locally with no internet connection required for inference.

### Step 7: Install LM Studio for a Graphical Interface

- Open a browser and navigate to `lmstudio.ai`.
- Click Download and install the application.
- Open LM Studio.
- On the left sidebar, choose between User, Power User, and Developer modes. Developer mode exposes the most controls and information.
- Click the search icon on the left to open the model search.
- Browse models, filter by category, and download the ones you want directly through LM Studio.
- Models downloaded in LM Studio are managed separately from Ollama unless linked with GoLLaMA.

### Step 8: Use GoLLaMA to Link Ollama Models Into LM Studio

- GoLLaMA is a macOS and Linux tool that lets LM Studio discover models already downloaded through Ollama. Windows users cannot use GoLLaMA and must download models separately in LM Studio.
- If you have Homebrew installed, run `brew install gollama` in the terminal.
- Once installed, run `gollama` in the terminal.
- A terminal-based selector appears showing all Ollama models, their exact file sizes, parameter counts, quantization methods, and model families.
- Select the model you want, press `L` to link it, and confirm.
- Return to LM Studio. The linked model now appears in the LM Studio model list and is ready to use inside the GUI.
- This avoids storing duplicate copies of large model files on disk.

### Step 9: Select Models Based on Your Hardware

- On Apple Silicon Macs with M1, M2, M3, or M4 chips, random access memory (RAM) is unified memory shared between the central processing unit (CPU) and the GPU, so total RAM is the main constraint.
- On Windows machines with an NVIDIA GPU, video random access memory (VRAM) is the main constraint. System RAM does not determine which models you can run.
- Allocate 2 GB of RAM per 1 billion parameters.
- A 96 GB MacBook with M3 can run a 120B model.
- If your machine has limited RAM (Apple Silicon) or limited VRAM (NVIDIA GPU), stick to models between 4B and 40B parameters.
- Use the Artificial Analysis benchmarks, which compare open-source models by category such as coding, general intelligence, and reasoning.

### Step 10: Understand Quantization to Run Larger Models

- Quantization reduces the precision of model weights, making the model file smaller so it can run on less powerful hardware.
- For example, reducing a model from 16-bit precision to 4-bit precision shrinks it by 70 percent while retaining its capability.
- A quantized model is not proportionally less capable. A model quantized to 4-bit is 20 percent less capable than the 16-bit version, not 70 percent less capable.
- Most users download pre-quantized models directly. If you need to create a custom quantized version, the workflow is: download the raw base model, apply any instruction fine-tuning you require, then quantize the resulting model.
- Use quantized models when storage space or RAM/VRAM is limited and you need to fit larger models onto consumer hardware.

## Examples

### Example 1: Run a Local Coding Assistant Without Internet

- Install Ollama and run `ollama run gpt-oss:20b`.
- Connect Cursor or another IDE to `http://localhost:11434/api/generate`.
- Write and refactor code with completions generated locally. No data is sent to an external API and no subscription is required.

### Example 2: Use a Local Model on a Flight

- With Ollama installed and a model such as `gpt-oss:20b` downloaded, disconnect from Wi-Fi.
- Run `ollama run gpt-oss:20b` in the terminal.
- Ask questions, draft emails, or brainstorm ideas entirely offline.
- Because the model runs on your machine, connectivity does not affect availability.

### Example 3: Build a Privacy-First Document Analyzer

- Download a model such as `gpt-oss:20b` with Ollama.
- Write a small script that sends document text to the local API at `http://localhost:11434/api/generate`.
- Summarize sensitive internal documents without sending them to any third-party service.
- Because nothing leaves your device, this workflow is suitable for private or regulated data.

## Best Practices

- ✅ Use models between 4B and 40B parameters on consumer hardware unless you have high-end memory or VRAM.
- ✅ Check `ollama list` regularly so you know which models are installed and how much space they use.
- ✅ Delete models you no longer need to free disk space and avoid working with outdated weights.
- ✅ Use GoLLaMA to share Ollama models with LM Studio instead of downloading the same file twice.
- ✅ Verify the exact model name with `ollama list` before calling the API to avoid "model not found" errors.
- ✅ Use quantization when hardware is limited so you can fit larger, more capable models locally.
- ✅ Compare models on Artificial Analysis benchmarks instead of guessing which model is best for coding, reasoning, or Q&A.

## Keep In Mind

- Open-source model quality improves with each release. The speaker says: "3 months ago in the open-source AI field is like three decades. This field is moving so fast." Models that were state of the art 3 months ago are already outdated.
- On Apple Silicon, total RAM governs which models you can run. On NVIDIA GPUs, VRAM governs which models you can run.
- Ollama is both a model downloader and a local API server. LM Studio is a GUI frontend. Both can download and run models, but using them together with GoLLaMA avoids duplication.
- Terminal-based interaction with Ollama is simple and fast. LM Studio provides a richer interface with chat history, token counts, and hardware usage metrics.

## Security & Safety Notes

- All inference happens on your machine when using Ollama or LM Studio locally. No prompts or responses are sent to external servers.
- Fine-tuned local models can be customized for sensitive or proprietary use cases without exposing data.
- Anyone with access to your machine can use the locally running models. Protect your device with appropriate authentication and disk encryption.
- Models downloaded from the internet should be sourced from trusted providers. Verify model provenance before running them on sensitive systems.

## Common Pitfalls

- **Problem:** The API returns a "model not found" error even though the model was downloaded.
  **Solution:** Run `ollama list` and use the exact model name shown in the output. Model tags such as `latest` matter and must match exactly.

- **Problem:** Running a large model is unacceptably slow or crashes the system.
  **Solution:** Use a smaller model or a more aggressively quantized version. Match the model parameter count to your available RAM or VRAM using the 2 GB per 1B parameter rule as a starting point.

- **Problem:** The same large model is stored twice on disk because it was downloaded in both Ollama and LM Studio.
  **Solution:** Install GoLLaMA and link Ollama models into LM Studio instead of downloading them separately in LM Studio.

- **Problem:** The terminal UI lacks chat history, token counts, and hardware usage metrics compared to cloud chat interfaces.
  **Solution:** Use LM Studio in Developer mode for a richer experience with chat histories, token usage, and model switching.

## Glossary

- **Artificial Analysis benchmarks**: Benchmarks that compare open-source models by category such as coding, general intelligence, and reasoning. According to the transcript, "artificial analysis did a really good metric and actually they keep updating this benchmark."
- **Quantization**: A process that reduces the precision of model weights to save space. According to the transcript, "quantization makes these weights less precise... It kind of normalizes these values. This is to save space. So a large model can run on a smaller less powerful computer." The speaker notes that a model made three times as small is "only 20% worse" in capability, while a 16-bit to 4-bit reduction shrinks the model by 70 percent.
- **SafeTensors**: An efficient file format for storing model weights on your computer. According to the transcript, "the safe tensors format is an efficient file format for storing these model weights on your computer."
