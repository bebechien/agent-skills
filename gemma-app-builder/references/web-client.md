# Web / Client App

This module focuses on building client-side applications where Gemma runs directly in the browser or on-device.

## Options

### 1. LiteRT-LM (formerly TensorFlow Lite for LLMs)
Optimized for on-device performance (Android, iOS, Web).

**Setup:**
-   **Convert**: Convert the Gemma checkpoint to `.tflite` format using the LiteRT converter.
-   **Integrate**: Use the LiteRT-LM C++ or Java API to load the model and run inference.
-   **Performance**: Leverages GPU and NPU acceleration.

**Example Prompt:**
"How do I convert a Gemma model to .tflite for use with LiteRT-LM?"

### 2. Transformers.js
Run Transformers directly in the browser using JavaScript.

**Setup:**
-   **Install**: `npm install @xenova/transformers`
-   **Load**:
    ```javascript
    import { pipeline } from '@xenova/transformers';
    const generator = await pipeline('text-generation', 'Xenova/gemma-2b-it');
    ```
-   **Run**: Generate text entirely client-side.

**Example Prompt:**
"Show me a code snippet to run Gemma in a React app using transformers.js."
