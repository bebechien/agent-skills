---
name: gemma-app-builder
description: Guide for building applications with Gemma, covering backend setup, RAG integration, client-side apps, and cloud deployment.
---

# Gemma App Builder

This skill helps you build applications using Gemma models. It provides a structured approach based on your deployment needs, from local backends to cloud scaling.

## Workflow

1.  **Backend/API**: "I want a backend/API"
    -   Use Ollama or LM Studio to serve the model locally.
    -   See [references/backend.md](references/backend.md)

2.  **RAG Integration**: "I want RAG"
    -   Add a frontend like AnythingLLM or OpenWebUI on top of your backend.
    -   See [references/rag.md](references/rag.md)

3.  **Web/Client App**: "I want a Web/Client App"
    -   Run models directly in the browser or on-device using LiteRT-LM or transformers.js.
    -   See [references/web-client.md](references/web-client.md)

4.  **Cloud Deployment**: "I want to run it on Cloud"
    -   Deploy your application using Vertex AI.
    -   See [references/cloud.md](references/cloud.md)

## Usage

Identify your goal and navigate to the corresponding module.

-   For local API: "How do I serve Gemma with Ollama?"
-   For RAG: "Connect AnythingLLM to my local Gemma."
-   For Client-side: "Run Gemma in the browser with transformers.js."
-   For Cloud: "Deploy Gemma to Vertex AI."
