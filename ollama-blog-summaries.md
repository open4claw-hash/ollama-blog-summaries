# Ollama Blog Summaries

A collection of recent Ollama blog posts covering new features, models, and integrations.

---

## 1. OpenClaw

**Date:** February 1, 2026  
**URL:** https://ollama.com/blog/openclaw

### Summary

OpenClaw is a personal AI assistant that bridges messaging platforms (WhatsApp, Telegram, Slack, Discord, iMessage) to AI coding agents through a centralized gateway. It runs locally on your own devices, keeping conversations and code private.

### Key Points

- **Install (Linux):** `curl -fsSL https://openclaw.ai/install.sh | bash`
- **Install (Windows):** `iwr -useb https://openclaw.ai/install.ps1 | iex`
- **Run:** `ollama launch openclaw`
- **Recommended Models (64k+ context):**
  - `qwen3-coder` — optimized for coding
  - `glm-4.7` — general purpose
  - `kimi-k2.5` — agentic tasks
  - `minimax-m2.1` — multilingual
- Previously known as **Clawdbot** and **Moltbot**

---

## 2. ollama launch

**Date:** January 23, 2026  
**URL:** https://ollama.com/blog/launch

### Summary

A new command that sets up and runs coding tools like Claude Code, OpenCode, and Codex with local or cloud models. No environment variables or config files needed.

### Key Points

- **One command setup:**
  - Claude Code: `ollama launch claude`
  - OpenCode: `ollama launch opencode`
- **Supported Integrations:** Claude Code, OpenCode, Codex, Droid
- **Requirements:** ~23 GB VRAM with 64k tokens context length
- **Recommended Models:**
  - Local: `glm-4.7-flash`, `qwen3-coder`, `gpt-oss:20b`
  - Cloud: `glm-4.7:cloud`, `minimax-m2.1:cloud`, `gpt-oss:120b-cloud`, `qwen3-coder:480b-cloud`
- **Configure only:** `ollama launch opencode --config`
- Extended 5-hour coding sessions available on Ollama Cloud

---

## 3. Image Generation (Experimental)

**Date:** January 20, 2026  
**URL:** https://ollama.com/blog/image-generation

### Summary

Ollama now supports image generation on macOS, with Windows and Linux coming soon. Uses text-to-image models to generate images directly from prompts.

### Key Points

- **Command:** `ollama run x/z-image-turbo "your prompt"`
- **Models Available:**
  - **Z-Image Turbo** (6B params, Alibaba's Tongyi Lab)
    - Photorealistic output
    - Bilingual text rendering (English & Chinese)
    - Apache 2.0 license
  - **FLUX.2 Klein** (Black Forest Labs)
    - 4B: Apache 2.0
    - 9B: FLUX Non-Commercial License v2.1
- **Configuration Options:**
  - Image size (`/set width`, `/set height`)
  - Number of steps
  - Random seed (for reproducibility)
  - Negative prompts
- Images save to current directory
- Terminals with image rendering (Ghostty, iTerm2) can preview inline
- **Coming Soon:** Windows/Linux support, more models, image editing

---

## 4. Claude Code with Anthropic API Compatibility

**Date:** January 16, 2026  
**URL:** https://ollama.com/blog/claude

### Summary

Ollama v0.14.0+ is now compatible with the Anthropic Messages API, making it possible to use Claude Code with open-source models. Run Claude Code with local or cloud models.

### Key Points

- **Install Claude Code:**
  - macOS/Linux: `curl -fsSL https://claude.ai/install.sh | bash`
  - Windows PowerShell: `irm https://claude.ai/install.ps1 | iex`
- **Connect to Ollama:**
  ```bash
  export ANTHROPIC_AUTH_TOKEN=ollama
  export ANTHROPIC_BASE_URL=http://localhost:11434
  ```
- **Run:** `claude --model gpt-oss:20b` or `claude --model glm-4.7:cloud`
- **Recommended Context:** 32K+ tokens
- **Supported Features:**
  - Messages & multi-turn conversations
  - Streaming
  - System prompts
  - Tool calling / function calling
  - Extended thinking
  - Vision (image input)
- Works with Python & JavaScript Anthropic SDKs

---

## 5. OpenAI Codex with Ollama

**Date:** January 15, 2026  
**URL:** https://ollama.com/blog/codex

### Summary

Open models can be used with OpenAI's Codex CLI through Ollama. Codex can read, modify, and execute code in your working directory using models like `gpt-oss:20b` or `gpt-oss:120b`.

### Key Points

- **Install Codex:** `npm install -g @openai/codex`
- **Start with Ollama:** `codex --oss`
- **Default Model:** `gpt-oss:20b`
- **Change Model:** `codex --oss -m gpt-oss:120b`
- **Cloud Models:** `codex --oss -m gpt-oss:120b-cloud`
- **Requirement:** 32K+ tokens context length
- Works with all Ollama Cloud models

---

## 6. OpenAI gpt-oss-safeguard

**Date:** October 29, 2025  
**URL:** https://ollama.com/blog/gpt-oss-safeguard

### Summary

Ollama partners with OpenAI and ROOST to bring gpt-oss-safeguard reasoning models for safety classification tasks. Available in 20B and 120B sizes, Apache 2.0 licensed.

### Key Points

- **Run the model:**
  - 20B: `ollama run gpt-oss-safeguard:20b`
  - 120B: `ollama run gpt-oss-safeguard:120b`
- **Highlights:**
  - Trained for safety reasoning (LLM input-output filtering, content labeling)
  - "Bring your own policy" — interprets your written policy
  - Reasoned decisions with full Chain-of-Thought visibility
  - Configurable reasoning effort (low/medium/high)
  - Apache 2.0 license — free for commercial use
- **Partners:** OpenAI + ROOST (Robust Open Online Safety Tools)

---

## 7. MiniMax M2

**Date:** October 28, 2025  
**URL:** https://ollama.com/blog/minimax-m2

### Summary

MiniMax M2 is available on Ollama Cloud — a model built for coding and agentic workflows. Ranks #1 among open-source models globally on Artificial Analysis intelligence index.

### Key Points

- **Run:** `ollama run minimax-m2:cloud`
- **Highlights:**
  - **Superior Intelligence:** #1 open-source model on Artificial Analysis
  - **Advanced Coding:** Multi-file edits, coding-run-fix loops, test-validated repairs
  - **Agent Performance:** Plans/executes complex toolchains (shell, browser, retrieval, code runners)
  - **Efficient Design:** 10B activated params (230B total) — lower latency & cost
- **Integrations:** VS Code, Zed, Droid, Cline, Roo Code, Codex
- **Cloud API:**
  ```bash
  export OLLAMA_API_KEY="your_api_key_here"
  curl https://ollama.com/api/chat \
    -H "Authorization: Bearer $OLLAMA_API_KEY" \
    -d '{"model": "minimax-m2", "messages": [{"role": "user", "content": "Write a snake game in HTML."}]}'
  ```

---

## 8. NVIDIA DGX Spark

**Date:** October 13, 2025  
**URL:** https://ollama.com/blog/nvidia-spark

### Summary

Ollama partnered with NVIDIA to ensure smooth performance on the new DGX Spark — a personal AI workstation powered by the NVIDIA GB10 Grace Blackwell Superchip.

### Key Points

- **Hardware:** NVIDIA GB10 Grace Blackwell Superchip
- **Performance:** 1 petaFLOP for local language models
- **Memory:** 128GB
- **Compatible Models:** Qwen, DeepSeek, Llama, Mistral, Gemma, Gpt-oss, and more
- Supports custom/fine-tuned models
- Optimized for: chat, document processing (RAG, OCR), code tasks, multimodal workflows

---

*Generated from Ollama Blog — February 2026*
