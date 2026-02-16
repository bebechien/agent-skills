# RAG Integration

This module helps you add Retrieval-Augmented Generation (RAG) capabilities to your Gemma backend using a frontend interface.

## Options

### 1. AnythingLLM
AnythingLLM is an all-in-one desktop application for RAG.

**Setup:**
-   **Install**: Download from [useanything.com](https://useanything.com).
-   **Connect**: In settings, select "Ollama" or "LM Studio" as the LLM provider.
-   **Vector DB**: Use the built-in LanceDB or connect an external one.
-   **Documents**: Upload PDFs or scrape websites to chat with your data.

**Example Prompt:**
"Guide me through connecting AnythingLLM to my local Ollama instance."

### 2. OpenWebUI
Open WebUI is an extensible, self-hosted UI for LLMs.

**Setup:**
-   **Install**: Run via Docker: `docker run -d -p 3000:8080 ...`
-   **Connect**: It automatically detects Ollama if running on the same host (or configure the URL).
-   **RAG**: Upload files directly in the chat interface to enable RAG.

**Example Prompt:**
"How do I set up Open WebUI with Docker and connect it to Gemma?"
