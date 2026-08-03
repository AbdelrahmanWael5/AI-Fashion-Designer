# 👔 AI Fashion Designer

**Conversational Multi-Agent Fashion Image Generation using Large Language Models and Fine-Tuned Stable Diffusion XL**

Official implementation of the **AI Fashion Designer** framework.

<p>

<a href="https://portfolio-psi-one-or9jrg8ci8.vercel.app/projects/fashion-text-to-image">
    <img src="https://img.shields.io/badge/Project%20Page-Website-blue">
</a>

<img src="https://img.shields.io/badge/Demo-Coming%20Soon-orange" alt="Demo">

</p>

---

# Overview

<p align="center">
    <img src="assets/framework.png" width="100%">
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
git clone https://github.com/<your_username>/AI-Fashion-Designer.git
cd AI-Fashion-Designer

conda create -n fashion-designer python=3.10
conda activate fashion-designer

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

Each clothing image is converted into a detailed textual description capturing attributes such as:

- Category
- Color
- Material
- Fit
- Neckline
- Sleeve Length
- Pattern

---

## Caption Preprocessing

The generated captions are cleaned and standardized through a preprocessing pipeline that:

- Removes noisy information
- Standardizes fashion terminology
- Normalizes attribute values
- Produces a unified prompt format

---

## Final Dataset

The resulting image-caption pairs are used for supervised fine-tuning of Stable Diffusion XL.

---

# Fine-Tuning Stable Diffusion XL

Stable Diffusion XL is adapted to the fashion domain using the prepared image-caption dataset.

Training follows the standard SDXL fine-tuning strategy:

- Frozen Variational Autoencoder (VAE)
- Frozen Dual Text Encoders
- Fine-Tuned UNet

This enables the model to learn detailed relationships between garment descriptions and visual appearance while preserving the strong visual priors of the pretrained model.

---

# Conversational Multi-Agent Framework

The second stage of the project introduces a conversational AI framework that removes the need for manual prompt engineering.

## Fashion Consultant Agent

The Fashion Consultant interacts naturally with users by:

- Understanding clothing requests
- Asking follow-up questions
- Providing fashion recommendations
- Collecting missing garment attributes

---

## Attribute Extractor Agent

The Attribute Extractor continuously analyzes the conversation to:

- Extract clothing attributes
- Detect user modifications
- Update the structured clothing representation
- Preserve previously collected information

---

## Structured Clothing Representation

The extracted attributes are stored as a structured clothing description.

Example:

```json
{
  "category": "Hoodie",
  "color": "Black",
  "material": "Cotton",
  "fit": "Oversized",
  "neckline": "Hooded",
  "sleeve_length": "Long",
  "pattern": "Solid"
}
```

The final representation is automatically converted into the prompt expected by the fine-tuned Stable Diffusion XL model.

---

# Inference

The complete inference pipeline follows the workflow below:

```text
User Request
      ↓
Fashion Consultant Agent
      ↓
Attribute Extractor Agent
      ↓
Structured Clothing Representation
      ↓
Prompt Generation
      ↓
Fine-Tuned Stable Diffusion XL
      ↓
Generated Fashion Image
```

Run inference using:

```bash
python app.py
```

---

# Demo

A demonstration video showcasing the complete conversational workflow will be released soon.

---

# Acknowledgements

This project builds upon several outstanding open-source projects, including:

- Stable Diffusion XL
- Hugging Face Diffusers
- Hugging Face Transformers
- Qwen2.5-VL
- LangGraph
- VITON-HD

We sincerely thank the authors for making their work publicly available.

---

# Citation

If you find this project useful, please consider citing it.

```bibtex
Coming soon.
```

---

# License

Coming soon.
