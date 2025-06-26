# TextGenerator
# 🧠 GPT-2 Text Generator using Gradio

This project provides a simple user interface to generate creative text using OpenAI's GPT-2 model. It uses the Hugging Face `transformers` library and `gradio` to build an interactive web-based app.

## 🚀 Features

- Generates coherent text from a given prompt
- Adjustable max length and temperature controls
- User-friendly Gradio interface
- Runs on CPU or GPU (if available)

## 🛠️ Requirements

Install the necessary libraries before running the project:

```bash
pip install gradio transformers torch
```

## 📦 How to Run

Simply run the `gpt2_gradio_app.py` script:

```bash
python gpt2_gradio_app.py
```

This will launch a local Gradio interface in your browser.

## 🧑‍💻 Code Overview

- Loads the pre-trained GPT-2 model and tokenizer from Hugging Face.
- Provides a text box to input a prompt.
- Users can adjust:
  - **Max Length**: Controls the length of the generated output.
  - **Temperature**: Controls the randomness of the output. (Higher = more creative)
- Displays generated text below the interface.

## 💡 Parameters Explained

| Parameter    | Description                                                                 |
|--------------|-----------------------------------------------------------------------------|
| Prompt       | Starting text for the model to continue generating from                    |
| Max Length   | Maximum number of tokens in the generated text (range: 50 to 300)          |
| Temperature  | Sampling randomness (range: 0.1 to 1.5). Lower = more predictable output    |

## 📷 Interface Preview

> The Gradio UI includes:
> - Prompt input box
> - Sliders for max length and temperature
> - Output box for generated text

## 📝 Example

Input Prompt:
```
Once upon a time in a distant galaxy
```

Generated Output:
```
Once upon a time in a distant galaxy, there was a planet inhabited by creatures made of pure energy...
```

## 📄 License

This project is licensed under the MIT License.

---

Built with ❤️ using [Hugging Face Transformers](https://huggingface.co/transformers/) and [Gradio](https://www.gradio.app/).
