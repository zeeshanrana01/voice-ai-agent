# LiveKit Voice AI Assistant (Python Agent + Next.js Web App)

A modern, full-duplex real-time voice AI assistant with ultra-low latency WebRTC streaming, intelligent turn-taking, and a sleek web interface.

---

## Architecture Overview

- **Python Voice Agent (`agent.py`)**:
  - **Speech-to-Text (STT)**: Deepgram Nova-3
  - **Large Language Model (LLM)**: Google Gemma 4 (31B IT)
  - **Text-to-Speech (TTS)**: Inworld TTS (Voice: *Ashley*)
  - **Audio Enhancement**: ai_coustics neural noise reduction
  - **Turn Detection**: LiveKit Turn Detector
- **Web Application (`web/`)**:
  - **Framework**: Next.js 14 (App Router, TypeScript)
  - **UI/UX**: Tailwind CSS, Glassmorphism, Lucide Icons
  - **Visualizer**: Reactive 2D/Canvas Audio Orb responding to live voice amplitude & agent states (`listening`, `thinking`, `speaking`)
  - **Features**: Real-time dual transcription feed, microphone mute/unmute, audio device switcher, and WebRTC participant token generation.

---

## Quick Start Guide

### Step 1: Start the Python Voice Agent Worker

Open your first terminal in the root directory:

```powershell
# Navigate to project root
cd C:\Users\Rana_Zeeshan\Desktop\AgenticAi\voice_agent

# Run agent in development mode
uv run python agent.py dev
```

*The agent will connect to your LiveKit Cloud server (`wss://voice-ai-icw8zgfs.livekit.cloud`) and stand by for calls.*

---

### Step 2: Start the Next.js Web Application

Open a second terminal:

```powershell
# Navigate to web directory
cd C:\Users\Rana_Zeeshan\Desktop\AgenticAi\voice_agent\web

# Start development server
npm run dev
```

---

### Step 3: Open and Talk to Your Agent

1. Open **[http://localhost:3000](http://localhost:3000)** in your browser.
2. Click **"Start Voice Conversation"**.
3. Allow microphone permissions when prompted.
4. The agent (**Ashley**) will greet you and begin conversational voice interaction!

---

## Project Structure

```
voice_agent/
├── agent.py                 # LiveKit Python agent worker definition
├── pyproject.toml           # Python dependencies (livekit-agents, ai-coustics)
├── .env                     # LiveKit Cloud API keys & secret
└── web/                     # Next.js 14 Modern Web App
    ├── src/
    │   ├── app/
    │   │   ├── api/
    │   │   │   └── connection-details/route.ts  # Token generation API
    │   │   ├── globals.css                      # Glassmorphism & custom styles
    │   │   ├── layout.tsx                       # App layout
    │   │   └── page.tsx                         # Voice assistant main page
    │   └── components/
    │       ├── AudioOrb.tsx                     # Reactive Canvas voice visualizer
    │       ├── ControlBar.tsx                   # Mic & device controls
    │       ├── TranscriptionView.tsx            # Live subtitles & chat drawer
    │       └── VoiceAssistant.tsx               # WebRTC room orchestrator
    ├── package.json
    ├── tailwind.config.ts
    └── tsconfig.json
```
