# 👔 AI Fashion Designer

**Conversational Multi-Agent Fashion Image Generation using Large Language Models and Fine-Tuned Stable Diffusion XL**

Official implementation of the **AI Fashion Designer** framework.

<p>

<a href="https://portfolio-psi-one-or9jrg8ci8.vercel.app/projects/fashion-text-to-image">
    <img src="https://img.shields.io/badge/Project%20Page-Website-blue">
</a>

<a href="ai_fashion_designer.pdf">
    <img src="https://img.shields.io/badge/Documentation-PDF-red">
</a>

<img src="https://img.shields.io/badge/Demo-Coming%20Soon-orange">

</p>

---

# Overview

<p align="center">
    <img src="assets/overall_framework.png" width="100%">
</p>

<p align="center">
<b>Figure 1.</b> End-to-end architecture of the AI Fashion Designer framework.
</p>

> **Abstract**
>
> AI Fashion Designer is an end-to-end conversational fashion image generation framework that combines Large Language Models with a fine-tuned Stable Diffusion XL model. Instead of requiring users to manually engineer prompts, the system employs a collaborative multi-agent architecture that interacts naturally with users, collects garment attributes through conversation, maintains a structured representation of the desired clothing, and automatically constructs the prompt required by the diffusion model.
>
> The framework consists of three major stages: automatic fashion dataset preparation, supervised fine-tuning of Stable Diffusion XL on a custom fashion image-caption dataset, and a conversational multi-agent framework that transforms natural language into high-quality fashion images.

---

# Requirements

Clone the repository and install the required dependencies.

```bash
git clone https://github.com/<your_username>/ai-fashion-designer.git
cd ai-fashion-designer

conda create -n ai-fashion-designer python=3.10
conda activate ai-fashion-designer

pip install -r requirements.txt
```

---

# Dataset Preparation

The fashion image generation model is trained on a custom image-caption dataset constructed from the **VITON-HD** dataset.

## VITON-HD

Download the VITON-HD dataset from its official repository.

https://github.com/shadow2496/VITON-HD

---

## Caption Generation

Garment captions are automatically generated using **Qwen2.5-VL**.

Each garment image is converted into a detailed textual description containing attributes such as:

- Category
- Color
- Material
- Fit
- Neckline
- Sleeve Length
- Pattern

---

## Caption Preprocessing

The generated captions are automatically cleaned and standardized to produce a consistent prompt format suitable for Stable Diffusion XL fine-tuning.

The preprocessing pipeline:

- Removes noisy information
- Normalizes attribute values
- Standardizes fashion terminology
- Produces unified image-caption pairs

---

## Final Dataset

The resulting image-caption pairs are used to fine-tune Stable Diffusion XL for fashion image generation.

---

# Fine-Tuning Stable Diffusion XL

Stable Diffusion XL is adapted to the fashion domain using the prepared image-caption dataset.

The fine-tuning strategy includes:

- Frozen Variational Autoencoder (VAE)
- Frozen Dual Text Encoders
- Fine-Tuned UNet

This enables the model to accurately generate clothing images that follow detailed garment descriptions while preserving the strong visual capabilities of the pretrained SDXL model.

---

# Conversational Multi-Agent Framework

The second stage introduces a conversational AI system that eliminates manual prompt engineering.

## Fashion Consultant Agent

The Fashion Consultant interacts naturally with users to:

- Understand clothing requests
- Ask follow-up questions
- Provide fashion recommendations
- Collect missing garment attributes

---

## Attribute Extractor Agent

The Attribute Extractor continuously analyzes the conversation and:

- Extracts clothing attributes
- Detects modifications
- Updates the structured clothing representation
- Preserves conversation context

---

## Structured Clothing Representation

All collected attributes are maintained within a shared structured representation.

Example:

```json
{
  "category": "Jacket",
  "color": "Brown",
  "material": "Leather",
  "fit": "Oversized",
  "neckline": "Collared",
  "sleeve_length": "Long",
  "pattern": "Solid"
}
```

Once all required attributes have been collected, the representation is automatically converted into the prompt format expected by the fine-tuned Stable Diffusion XL model.

---

# Inference Pipeline

The complete inference workflow is illustrated below.

```text
User Request
        │
        ▼
Fashion Consultant Agent
        │
        ▼
Attribute Extractor Agent
        │
        ▼
Structured Clothing Representation
        │
        ▼
Prompt Builder
        │
        ▼
Fine-Tuned Stable Diffusion XL
        │
        ▼
Generated Fashion Image
```

Run the application using:

```bash
python app.py
```

---

# Project Structure

```text
ai-fashion-designer/

├── app.py
├── inference.py
├── requirements.txt

├── agents/
│   ├── fashion_consultant.py
│   ├── attribute_extractor.py
│   ├── prompt_builder.py
│   └── ...

├── dataset/
│
├── preprocessing/
│
├── training/
│
├── models/
│
├── assets/
│
└── README.md
```

---

# Acknowledgements

This project builds upon several outstanding open-source projects.

- Stable Diffusion XL
- Hugging Face Diffusers
- Hugging Face Transformers
- LangGraph
- Qwen2.5-VL
- VITON-HD

We sincerely thank the authors for making their work publicly available.

---

# Citation

If you find this project useful, please consider citing the accompanying documentation.

```bibtex
Coming soon.
```

---

# License

Coming soon.
