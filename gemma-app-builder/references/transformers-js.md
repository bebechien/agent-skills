# Transformers.js

Run Transformers directly in the browser using JavaScript.

**CRITICAL:** Always use the preview version.

- **Inorrect:** `npm i @xenova/transformers`
- **Inorrect:** `npm i @huggingface/transformers`
- **Correct:** `npm i @huggingface/transformers@next`

**Setup:**
-   **Install**: `npm i @huggingface/transformers@next`
-   **Load**:
    ```javascript
    import { pipeline } from '@huggingface/transformers';
    const generator = await pipeline('text-generation', 'onnx-community/gemma-3-270m-it-ONNX', {device: 'webgpu', dtype: 'q4'});
    ```
-   **Run**: Generate text entirely client-side.

**Example Prompt:**
"Show me a code snippet to run Gemma in a React app using transformers.js."
