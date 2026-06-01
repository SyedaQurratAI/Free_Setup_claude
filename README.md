# Free_Setup_claude
# Qwen CLI is Dead. Gemini CLI Dies June 16. Here's Your Free Claude Code Setup That Actually Works.

**Author:** Syeda Qurrat-ul-Ain — GIAIC trained developer and Anthropic MCP certified developer from Karachi, Pakistan.  
*Why this guide?* After Qwen and Gemini CLI shut down, I needed a reliable, **free** way to keep using Claude Code. OpenRouter provides that solution.

---

## Why Claude Code + OpenRouter Is the Best Free Alternative

- **Zero cost**: No subscription fees; just an OpenRouter account.  
- **Broad model access**: Free tiers of Sonnet, Opus, Haiku, and many others.  
- **Seamless CLI experience**: All the familiar `claude` commands work unchanged.  
- **WSL-friendly**: Works perfectly on Ubuntu inside Windows Subsystem for Linux.

---

## Prerequisites

1. **WSL Ubuntu** (latest distribution).  
2. **OpenRouter account** – sign up at https://openrouter.ai and generate an API key.  
3. Basic familiarity with the Linux command line.

---

## Step-by-Step Setup Guide

### 1. Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

Or using the official install script:

```bash
curl -s https://claude.ai/cli.sh | sh
```

### 2. Create/Open the `.claude` Folder

```bash
mkdir -p ~/.claude
```

This folder holds your Claude Code settings.

### 3. Configure `settings.json` with OpenRouter Key

Create or edit `~/.claude/settings.json`:

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://openrouter.ai/api",
    "ANTHROPIC_AUTH_TOKEN": "sk-or-your-key-here",
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_MODEL": "openrouter/free"
  },
  "model": "sonnet[1m]"
}
```

**⚠️ Important Rules:**

- **DO NOT** add `/v1` to `ANTHROPIC_BASE_URL` – use exactly `https://openrouter.ai/api`  
- **DO NOT** use `ANTHROPIC_API_KEY` – the key must go in `ANTHROPIC_AUTH_TOKEN`  
- **DO NOT** modify shell config files (`~/.bashrc`, `~/.zshrc`, etc.) to set these variables – use `settings.json` only  

### 4. Verify the Setup

In the same terminal, run:

```bash
claude --version
```

If you see version information without errors, the setup is correct.

### 5. Open New Terminal and Run Claude

Close your current terminal and open a fresh one. Then:

```bash
claude
```

You should be dropped into the Claude Code interactive prompt.

---

## How to Switch Models on OpenRouter (Free Models Available)

To use a different model, specify it with the `--model` flag:

```bash
claude --model meta-llama/llama-3.2-3b-instruct:free
```

Popular **free** models on OpenRouter:

- `anthropic/claude-3-5-haiku-20241022`  
- `anthropic/claude-3-5-sonnet-20241022`  
- `meta-llama/llama-3.2-3b-instruct:free`  
- `google/gemini-2.0-flash-exp:free`  
- `deepseek/deepseek-chat`  

See the full list at: https://openrouter.ai/models?free=true

---

## Common Errors & Fixes

| Error | Cause | Solution |
|-------|-------|----------|
| `ANTHROPIC_API_KEY` error | Wrong env var used | Use `ANTHROPIC_AUTH_TOKEN` instead |
| `Could not resolve host` | Incorrect base URL | Use `https://openrouter.ai/api` (no `/v1`) |
| Auth failed / 401 | Invalid key | Double-check your OpenRouter API key |
| Command not found | Claude not in PATH | Reopen terminal or add to PATH |
| Empty responses / 429 | Rate limiting | Switch to another free model |

---

## Credits

The original setup concept was adapted from the open-source community documentation on Claude Code + OpenRouter integrations.

---

## Connect With Author

- **GitHub:** [@SyedaQurratAI](https://github.com/SyedaQurratAI)  
- **Portfolio:** [qurrat-portfolio.vercel.app](https://qurrat-portfolio.vercel.app)

