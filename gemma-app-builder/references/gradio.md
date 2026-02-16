# Gradio Web App

This module guides you in building interactive web interfaces for Gemma using the Gradio library and Hugging Face Transformers.

## Options

### 1. Gradio
Gradio allows you to quickly create UIs for your machine learning models in Python.

**Setup:**
-   **Prerequisites**:
    -   Ensure you have access to the Gemma model on Hugging Face (accept the license).
    -   Login to Hugging Face CLI:
        ```bash
        huggingface-cli login
        ```

-   **Install**:
    ```bash
    pip install gradio transformers torch accelerate
    ```

-   **Code**: Create `app.py`:
    ```python
    import gradio as gr
    from transformers import pipeline
    import torch

    # Load the pipeline
    # Replace "google/gemma-2-2b-it" with "google/gemma-3-1b-it" or other available models
    model_id = "google/gemma-2-2b-it"

    pipe = pipeline(
        "text-generation",
        model=model_id,
        model_kwargs={"torch_dtype": torch.bfloat16},
        device_map="auto",
    )

    def chat(message, history):
        messages = []
        # Add conversation history
        for user_msg, assistant_msg in history:
            messages.append({"role": "user", "content": user_msg})
            messages.append({"role": "assistant", "content": assistant_msg})
        # Add current user message
        messages.append({"role": "user", "content": message})

        # Generate response
        outputs = pipe(messages, max_new_tokens=256)
        # Return only the newly generated text
        return outputs[0]["generated_text"][-1]["content"]

    # Create the ChatInterface
    demo = gr.ChatInterface(
        fn=chat,
        title="Gemma Chatbot",
        description="Ask Gemma anything!",
    )

    if __name__ == "__main__":
        demo.launch()
    ```

-   **Run**:
    ```bash
    python app.py
    ```

**Example Prompt:**
"Write a Python script to create a Gradio interface for Gemma using the transformers library."
