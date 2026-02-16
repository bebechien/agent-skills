# Backend / API

This module guides you in setting up a local backend or API for Gemma using Ollama or LM Studio.

## Options

### 1. Ollama
Ollama is a lightweight tool to run LLMs locally.

**Setup:**
-   **Install**: Download from [ollama.com](https://ollama.com).
-   **Pull Gemma**: `ollama pull gemma3:1b`
-   **Run**: `ollama run gemma3:1b`
-   **API**: Runs on `http://localhost:11434`.

**Example Prompt:**
"Show me how to run Gemma with Ollama and access the API."

### 2. LM Studio
LM Studio provides a GUI for discovering and running local LLMs.

**Setup:**
-   **Install**: Download from [lmstudio.ai](https://lmstudio.ai).
-   **Search**: Find "Gemma" in the search bar.
-   **Download**: Select a quantization level and download.
-   **Serve**: Go to the "Local Server" tab and start the server.
-   **API**: Compatible with OpenAI's API format.

**Example Prompt:**
"How do I load Gemma in LM Studio and start the local server?"
