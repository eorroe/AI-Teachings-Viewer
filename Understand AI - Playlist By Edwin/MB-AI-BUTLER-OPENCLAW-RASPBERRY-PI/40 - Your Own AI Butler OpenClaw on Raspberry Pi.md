# Your Own AI Butler: OpenClaw on Raspberry Pi

## Overview

This teaching guides you through setting up OpenClaw, a locally hosted persistent AI assistant, on a Raspberry Pi 5 so you can interact with it through Telegram and run automated cron jobs. The speaker describes it as "perpetually running on a hardware" — a credit-card-sized device that can deliver morning briefings, job recommendations, and interactions enhanced by temperature sensors, cameras, and pressure sensors. It covers flashing Raspberry Pi OS with SSH and Wi-Fi preconfigured, installing OpenClaw on the Pi, provisioning a Telegram bot through BotFather, wiring API keys for Moonshot Kimi K2.5 and optional speech services, and activating skills like session memory.

## When to Follow These AI Teachings

- When you want a self-hosted persistent AI assistant on a Raspberry Pi instead of paying for Mac mini or VPS hosting.
- When you need an AI bot reachable via Telegram for on-the-go messaging.
- When you want to attach sensors to an LLM so it can react to temperature, camera, or pressure input.
- When you want to automate cron jobs like morning news digests or job searches running 24/7 on a local device.

## Steps

### Step 1: Gather Hardware

- Use a Raspberry Pi 5.
- Get a microSD card for reliable OpenClaw installation and operation.
- Use a power brick rated for up to 25 watts: 5 volts at 5 amps. The Pi will not draw 25 watts continuously, but the headroom is important for stability.

### Step 2: Flash Raspberry Pi OS With Preconfigured SSH and Wi-Fi

- Download the Raspberry Pi Imager from Google onto your computer.
- Install and open the Imager.
- Select the 64-bit Raspberry Pi OS image.
- Select your microSD card as the target storage.
- Set a hostname for the Pi (e.g., Jansky).
- Select your country and time zone.
- Enter your Wi-Fi SSID and password so the Pi connects automatically on boot.
- Enable SSH in the settings.
- Write the image to the SD card and wait for completion.

### Step 3: Boot the Pi and Connect via SSH

- Insert the flashed microSD card into the Raspberry Pi.
- Connect the 5V 5A power brick to power on the Pi.
- Wait for it to connect to your Wi-Fi.
- Find the Pi's IP address by SSHing with its hostname or by running `ip addr` after first login.
- SSH from your laptop using `ssh pi@Jansky` or `ssh pi@192.168.40.249`.
- Accept the host key fingerprint when prompted by typing `yes`.
- Enter the password. The default password is the same as the hostname (`Jansky`).
- Confirm you are inside the Pi by running `whoami` or checking the hostname.

### Step 4: Install OpenClaw on the Pi

- Visit moldbot.dev to get the one-liner install command.
- Paste and run the command in the Pi terminal.
- The installer will fetch NodeJS, npm, git, and OpenClaw dependencies automatically. The speaker notes: "The Pi's OS already includes many required packages, so setup completes quickly."
- Confirm the success message before proceeding.

### Step 5: Complete Onboarding and Accept the Warning

- Launch OpenClaw after installation to reach the onboarding screen.
- Accept the warning about running the agent in a sandboxed environment where you control access to personal data. The speaker says: "we are running this on a cheap Raspberry Pi... it's basically a computer in itself. It's just literally size of your credit card."
- Complete the onboarding prompts to configure the bot.

### Step 6: Configure the Moonshot AI API Key and Model

- Open the Moonshot AI console platform and create a new API key.
- Name the key a descriptive name like `Jensen keybot`.
- Copy the generated API key and recharge account credits. The speaker recharged their account with $10 before testing.
- Paste the API key into the OpenClaw onboarding prompt.
- When prompted for the model, change from the pre-selected Kimi K2 the0905 model to Kimi K2.5 by typing the model name and confirming.

### Step 7: Set Up the Telegram Messaging Service

- In the onboarding flow, select Telegram as the messaging service.
- Open Telegram and search for `@BotFather`.
- Start a chat with BotFather and send the `/newbot` command.
- Provide a display name for the bot (e.g., Jensen).
- Provide a unique username ending in `bot` (e.g., `Jensbot_bot`).
- Copy the access token BotFather provides.
- Paste the access token back into the OpenClaw onboarding screen.
- Confirm the token was accepted.

### Step 8: Install Homebrew and Choose Package Manager

- When prompted, confirm installation of Homebrew. OpenClaw skills require Homebrew for package management and installation.
- Select npm as the preferred package manager for installing additional skills.

### Step 9: Configure Optional Skills and API Keys

- From the list of skills shown during onboarding, enable only the `session-memory` skill to retain context across sessions. Leave all other skills disabled unless you have a specific integration planned.
- To enable voice transcription, generate an OpenAI Whisper API key and enter it when prompted.
- To enable text-to-speech responses, generate an ElevenLabs API key and enter it when prompted.
- Optionally add a Google API key, image generation key, or keys for other services you plan to integrate.
- Skip Apple Notes, Apple Reminders, or other skills you do not plan to use.

### Step 10: Configure Hooks and Memory

- When asked whether to log all comments, decline unless you have a specific need, as it increases memory usage.
- Enable session memory for new commands so the bot retains context across sessions.
- Confirm these settings before continuing.

### Step 11: Install the Gateway Service

- Proceed with the gateway installation when prompted. This starts a local web server that exposes the OpenClaw GUI at a `http://<pi-ip>:<port>` URL, letting you access it from other devices on your local network.
- Wait for the gateway installation to finish.

### Step 12: Interact With the Bot in Terminal

- Choose to hatch or chat with the bot in the terminal interface.
- Send messages and verify that Kimi K2.5 responds through OpenClaw on the Pi.
- Confirm voice and text-to-speech work if you configured those keys.

### Step 13: Set Up Automated Cron Jobs

- Create cron jobs on the Pi using `crontab -e`. Each job calls a shell script or OpenClaw command that fetches content such as tech headlines, astronomy updates, world news, weather, research papers, or job listings and sends a Telegram message.
  - Example: A morning cron job using `crontab` entry `0 7 * * * /path/to/morning-briefing.sh` that runs every morning. The job queries for tech headlines, astronomy updates, world news summaries, local weather, and new research papers.
- OpenClaw compiles a concise briefing and sends it to you through Telegram.
  - Example: A job-recommendation cron job that queries LinkedIn, Indeed, or a job API for roles matching your specified job titles (e.g., "AI Engineer", "Python Developer") and sends job recommendations via Telegram.
- Use the bot's command system to trigger these jobs on schedule without manual intervention.

### Step 14: Expand With Sensors

- Physically attach sensors to the Raspberry Pi GPIO pins using the GPIO header (pins 1-40). Sensor choices include: temperature sensors on GPIO4, a camera on the CSI port, or a pressure sensor via an ADC (e.g., MCP3008) on SPI pins.
- Install the `gpiozero` Python library to read sensor data. Write a Python script that reads the sensor value and triggers an OpenClaw notification if the reading exceeds your threshold.
- Configure OpenClaw skills or cron jobs to call your sensor-reading script and include the data as context in conversations or automated tasks. The speaker says this "transforms the bot from a chat interface into an environment-aware butler."

## Examples

### Example 1: Morning News Briefing Bot

- Configure a cron job using `crontab -e` with entry `0 7 * * * /path/to/morning-briefing.sh` that runs every morning. The job queries for tech headlines, astronomy updates, world news summaries, local weather, and new research papers.
- OpenClaw compiles a concise briefing and sends it to you through Telegram.

### Example 2: Job Search Automation

- Configure a cron job that runs periodically.
- The job queries LinkedIn, Indeed, or a job API for roles matching your specified job titles (e.g., "AI Engineer", "Python Developer").
- OpenClaw sends job recommendations through Telegram.
- You can review and apply directly from your phone.

### Example 3: Sensor-Augmented Assistant

- Attach a temperature sensor to GPIO4 on the Raspberry Pi, or a camera to the CSI port.
- Install the `gpiozero` Python library and write a script that reads the sensor value and triggers an OpenClaw notification if the temperature exceeds your threshold.
- Extend this to cameras (motion detection) or pressure sensors for environment-aware automations that OpenClaw acts on.

## Best Practices

- Use a 5V 5A power brick even though the Pi does not draw 25 watts continuously. It prevents instability under peak loads.
- Preconfigure SSH and Wi-Fi during imaging so you don't need to attach a monitor or keyboard to the Pi.
- Do not share your API keys publicly. The creator explicitly replaced keys after recording; you should do the same.
- Recharge your Moonshot account before testing to avoid failed requests during setup. The speaker recharged their account with $10 before testing.
- Enable only the skills you plan to use (for example, `session-memory`, `openai-whisper`, `elevenlabs-tts`). Logging all comments increases Pi memory usage.
- Name your host and bot something memorable so SSH and Telegram commands are easy to type.
- Run the bot in a safe or sandboxed environment during initial testing to avoid unintended actions.

## Keep In Mind

- OpenClaw runs locally on the Pi, but it still calls out to Moonshot's Kimi K2.5 API for model inference, so your prompts leave the device.
- The Raspberry Pi OS image should be 64-bit to match OpenClaw's NodeJS and dependency requirements.
- Telegram bot usernames must end in `bot` and must be globally unique.
- Gateway installation starts a local web server that exposes the OpenClaw GUI at `http://<pi-ip>:<port>`, accessible from devices on the same local network. It does not expose the GUI to the public internet by default.
- Cron jobs run on the Pi's system clock, which syncs via Network Time Protocol (NTP) once the Pi has internet access.

## Security & Safety Notes

- Treat your Moonshot API key, OpenAI API keys, and ElevenLabs API keys as secrets. Store them securely and never commit them to version control.
- Replace or rotate any key that was accidentally exposed during recording or debugging.
- The OpenClaw onboarding warning about safe environments is intentional. Review what tools and skills you grant before enabling integrations that can write files, run shell commands, or access external accounts.
- SSH is enabled by default after imaging. Ensure your Wi-Fi network uses a strong password and change the Pi's default login password if the hostname is predictable.
- Use a dedicated Moonshot account or API key for the Pi so you can isolate spending and permissions from your personal devices.

## Common Pitfalls

- **Problem:** Forgetting to enable SSH during the Raspberry Pi Imager setup, which forces you to attach a monitor and keyboard.
  **Solution:** Enable SSH in the Imager services tab before writing the image. This lets you SSH immediately after boot.

- **Problem:** Entering the wrong model name when switching from Kimi K2 to Kimi K2.5.
  **Solution:** Copy the model name from Moonshot's documentation and paste it into the onboarding prompt. Confirm by pressing enter and checking the bot's displayed model.

- **Problem:** Telegram bot username already taken.
  **Solution:** Try variations of your desired username with unique suffixes until BotFather accepts one.

- **Problem:** Gateway service or skills fail to install due to missing Homebrew.
  **Solution:** Install Homebrew during onboarding and confirm npm as the package manager. Re-run the installer if necessary.

- **Problem:** Running out of Moonshot API credits during setup.
  **Solution:** Pre-recharge your account before starting onboarding. The speaker recharged their account with $10 before testing.

- **Problem:** Logging all comments increases Pi memory usage.
  **Solution:** Decline comment logging unless required. Enable only session memory for new commands to keep memory usage low.

## Glossary

- **OpenClaw**: A locally hosted persistent AI assistant that runs on a Raspberry Pi, interacts through Telegram, and executes automated cron jobs. Formerly called CloudBot. The speaker describes it as "perpetually running on a hardware."
- **Sensor-augmented interactions**: Connecting physical sensors (temperature sensors, cameras, pressure sensors) to the Raspberry Pi GPIO pins so that OpenClaw can react to real-world inputs. The speaker says this "transforms the bot from a chat interface into an environment-aware butler."
