# Install required libraries (if not already installed)
# !pip install gradio transformers torch

import gradio as gr
from transformers import GPT2LMHeadModel, GPT2Tokenizer
import torch

# Load model and tokenizer
tokenizer = GPT2Tokenizer.from_pretrained('gpt2')
model = GPT2LMHeadModel.from_pretrained('gpt2')

# Move model to GPU if available
device = 'cuda' if torch.cuda.is_available() else 'cpu'
model = model.to(device)

# Define the text generation function
def generate_text_gpt2(prompt, max_length=100, temperature=1.0):
    input_ids = tokenizer.encode(prompt, return_tensors='pt').to(device)
    attention_mask = torch.ones(input_ids.shape, device=device)

    output = model.generate(
        input_ids,
        attention_mask=attention_mask,
        max_length=max_length,
        temperature=temperature,
        do_sample=True,
        num_return_sequences=1,
        pad_token_id=tokenizer.eos_token_id
    )

    generated_text = tokenizer.decode(output[0], skip_special_tokens=True)
    return generated_text

# Build the Gradio interface
iface = gr.Interface(
    fn=generate_text_gpt2,
    inputs=[
        gr.Textbox(label="Enter Prompt", placeholder="Type something..."),
        gr.Slider(50, 300, value=100, step=10, label="Max Length"),
        gr.Slider(0.1, 1.5, value=1.0, step=0.1, label="Temperature")
    ],
    outputs=gr.Textbox(label="Generated Text"),
    title="GPT-2 Text Generator",
    description="Generate creative text using OpenAI's GPT-2 model."
)

# Launch the interface
iface.launch()
