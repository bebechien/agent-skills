---
name: gemma-app-builder
description: Guide for building applications with Gemma, covering backend setup, RAG integration, client-side apps, and cloud deployment.
---

# Gemma App Builder

This documentation provides a structured approach to building, integrating, and deploying applications using the Gemma family of models.

## CORE PRINCIPLE: The "Abstraction First" Rule

**DO NOT** generate raw PyTorch, TensorFlow, or `transformers` code unless the user explicitly asks for "Training", "Fine-tuning", or "Research". Prioritize high-level tooling and frameworks for application building.

## Model Selection

**CRITICAL:** Do not default to `gemma-3-1b-it` every request. Carefully analyze the user's specific domain, required input modalities (text, image, audio), and technical constraints to recommend the correct variant.

### 1. Core Gemma 3 Models (By Capability)

Use this table to select a model based on hardware limits and required input modalities.

| Model Size / Variant | Supported Inputs | Context Length | Best Used For |
| --- | --- | --- | --- |
| **Gemma 3 (270m / 1B)** | Text only | 32k tokens | Fast, lightweight text generation and general language tasks in resource-constrained environments. |
| **Gemma 3 (4B / 12B / 27B)** | Text & Image | 128k tokens | Advanced multimodal reasoning, vision tasks, and analyzing large document contexts. |
| **Gemma 3n (E2B / E4B)** | Text, Image & **Audio** | Standard Mobile | Mobile apps (NPU acceleration) or any workflow specifically requiring **audio input**. |

### 2. Task-Specific Variants

For specialized workflows, avoid forcing a standard model to do the work. Use these purpose-built variants instead.

| If User Wants... | ❌ Don't Use | ✅ USE THIS VARIANT | Why? |
| --- | --- | --- | --- |
| **"Summarize this 100-page PDF"** | Gemma 3 (Decoder-only) | **T5Gemma 2 (270m/1B/4B)** | Encoder-Decoder architecture handles long-context summarization far better than standard LLMs. |
| **"Analyze Medical/CT/MRI Data"** | Standard Gemma | **MedGemma 1.5** | Specialized for 3D medical imaging (DICOM) and EHR analysis. |
| **"Function Calling / Agent Actions"** | Prompt Engineering | **FunctionGemma** | Fine-tuned specifically for structured JSON output and reliable tool use. |
| **"Search / RAG Embeddings"** | Gecko / BERT | **EmbeddingGemma** | Dedicated embedding model supporting up to 2k tokens with flexible output dimensions (from 768 down to 128). |
| **"Safety / Content Moderation"** | Python Rules | **ShieldGemma 2** | A classification model designed to run *in parallel* with your main chat model to ensure output safety. |

## Deployment Workflows

This framework provides a structured approach depending on your target environment, scaling from local prototypes to cloud-native deployments.

### 1. Backend & API Services
* **Goal:** "I want a backend/API."
* **Action:** Serve the model locally using tools like **Ollama** or **LM Studio**.
* **Reference:** `[references/backend.md](references/backend.md)`

### 2. RAG (Retrieval-Augmented Generation)
* **Goal:** "I want to chat with my documents."
* **Action:** Layer a frontend application like **AnythingLLM** or **OpenWebUI** on top of your local backend.
* **Reference:** `[references/rag.md](references/rag.md)`

### 3. Web & Client Applications
* **Goal:** "I want a Web/Client App."
* **Action:** Run models natively on-device or directly in the browser utilizing **LiteRT-LM** or **transformers.js**.
* **Reference:** `[references/web-client.md](references/web-client.md)`

### 4. Cloud Deployment
* **Goal:** "I want to run it on Cloud at scale."
* **Action:** Containerize and deploy your Gemma application using **Vertex AI**.
* **Reference:** `[references/cloud.md](references/cloud.md)`

### 5. Prototyping & Demos
* **Goal:** "I want to prototype quickly with Python."
* **Action:** Build interactive web interfaces using **Gradio** and **Transformers**.
* **Reference:** `[references/gradio.md](references/gradio.md)`
