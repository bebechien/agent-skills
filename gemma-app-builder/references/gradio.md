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
    from transformers import pipeline, TextIteratorStreamer
    from threading import Thread

    # Load the pipeline
    # Replace "google/gemma-3-1b-it" with other available models
    model_id = "google/gemma-3-1b-it"

    pipe = pipeline(
        "text-generation",
        model=model_id,
        device_map="auto",
        dtype="auto",
    )

    def chat(message, history):
        messages = []
        # Add conversation history
        for user_msg, assistant_msg in history:
            messages.append({"role": "user", "content": user_msg})
            messages.append({"role": "assistant", "content": assistant_msg})
        # Add current user message
        messages.append({"role": "user", "content": message})

        streamer = TextIteratorStreamer(pipe.tokenizer, skip_prompt=True, skip_special_tokens=True)
        thread = Thread(target=pipe, args=(messages,), kwargs=dict(
            max_new_tokens=256,
            streamer=streamer
        ))
        thread.start()

        # Generate response
        generated_text = ""
        for new_text in streamer:
            generated_text += new_text
            yield generated_text

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
