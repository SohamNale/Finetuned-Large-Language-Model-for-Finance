# Finetuned-Large-Language-Model-for-Finance

This project fine-tunes the LLaMA 2 7B model on banking-related queries to create a specialized banking assistant. The implementation uses PEFT (Parameter Efficient Fine-Tuning) techniques and is optimized to run on Google Colab with T4 GPU.

## Overview

The project consists of two main components:
1. Model fine-tuning pipeline (Running_code_1.ipynb)
2. Inference application (Running_Code_Final.ipynb)

The model is trained on a custom banking dataset (Banking.csv) containing various banking-related questions and their detailed responses.

## Requirements

- Google Colab with T4 GPU
- Python 3.10+
- PyTorch
- Transformers
- PEFT
- Accelerate
- Bitsandbytes
- Gradio

## Project Structure
```sh
📁 banking-llm/
│
├── 📁 data/
│   └── Banking.csv                # Banking Q&A dataset with question-answer pairs
│
├── 📁 notebooks/
│   ├── Running_code_1.ipynb      # Training pipeline notebook
│   └── Running_Code_Final.ipynb   # Inference and demo application notebook
│
├── 📁 models/                     # Directory for saved model weights
│   └── adapter/                   # LoRA adapter weights directory
│
└── README.md                      # Project documentation
```

## Setup & Training

1. Upload all files to Google Colab
2. Open `Running_code_1.ipynb` and run all cells to:
   - Install dependencies
   - Load and preprocess the banking dataset
   - Initialize the LLaMA 2 7B model with 4-bit quantization
   - Fine-tune using LoRA adapter
   - Save the trained adapter weights

## Running the Assistant

1. Open `Running_Code_Final.ipynb` in Google Colab
2. Run all cells to:
   - Load the base LLaMA 2 7B model
   - Load the fine-tuned adapter weights
   - Start the Gradio interface for interactive querying

## Model Details

- Base Model: LLaMA 2 7B (Guanaco Instruct variant)
- Training Method: LoRA (Low-Rank Adaptation)
- Quantization: 4-bit quantization using bitsandbytes
- Training Parameters:
  - LoRA rank: 64
  - LoRA alpha: 16
  - Dropout: 0.1
  - Learning rate: 2e-4
  - Batch size: 4
  - Max sequence length: 512

## Usage

After starting the Gradio interface, simply:
1. Enter your banking-related question in the text input
2. Click submit
3. Get a detailed, context-aware response from the model

## Limitations

- Requires T4 GPU or better for reasonable performance
- Model responses are limited to banking domain knowledge
- Requires internet connection for downloading model weights

## Acknowledgments

- Meta AI for LLaMA 2
- Hugging Face for the Transformers library
- Microsoft for LoRA implementation
