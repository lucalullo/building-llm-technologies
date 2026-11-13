# Building LLM Technologies

A collection of minimal educational notebooks that isolate and explain core technologies used inside modern LLMs.

Each version focuses on one mechanism, uses small numbers and short code, and prefers pure Python whenever a library would hide the concept being studied.

> **One notebook, one technology, one clear idea.**

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white) ![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) [![Kaggle Notebook](https://img.shields.io/badge/Kaggle-Notebook-20BEFF?logo=kaggle&logoColor=white)](https://www.kaggle.com/code/lucalullo/building-llm-technologies)

[Kaggle notebook](https://www.kaggle.com/code/lucalullo/building-llm-technologies) · [GitHub repository](https://github.com/lucalullo/building-llm-technologies) · [Technical report](project-report-en.pdf)

![Project roadmap and architecture](infographic.png)

## Overview

The goal is not to build another complete language model. The companion project [Building LLM](https://github.com/lucalullo/building-llm) already follows that path from statistical counts to a small decoder-only Transformer.

**Building LLM Technologies** takes the opposite approach: it isolates individual mechanisms so they can be understood independently.

The notebooks answer questions such as:

- Why does a decoder-only LLM need a causal mask?
- How does the model represent token order?
- Why are multiple attention heads useful?
- What do residual connections and LayerNorm do?
- What happens inside a Transformer block?
- How do logits become probabilities?
- How do temperature, top-k and top-p affect generation?

## Learning modules

| Version | Technology | Main idea |
|---|---|---|
| 1 | Causal Mask | Prevent attention from using future positions |
| 2 | Positional Encoding | Add sequence-position information to token representations |
| 3 | Multi-Head Attention | Use multiple attention views in parallel |
| 4 | Residual Connection | Preserve the previous representation while adding new information |
| 5 | Layer Normalization | Keep internal activations on a stable scale |
| 6 | Feed-Forward Network | Transform each token independently after attention |
| 7 | Transformer Block | Combine attention, residuals, normalization and feed-forward processing |
| 8 | Logits and Softmax | Turn model scores into next-token probabilities |
| 9 | Temperature | Rescale logits before softmax to control distribution sharpness |
| 10 | Top-k and Top-p Sampling | Restrict the candidate tokens used for generation |

## Architecture

```text
Input tokens
    ↓
Positional information
    ↓
Transformer processing
    ├── Causal Mask
    ├── Multi-Head Attention
    ├── Residual Connection
    ├── Layer Normalization
    └── Feed-Forward Network
    ↓
Transformer Block output
    ↓
Logits
    ↓
Temperature scaling
    ↓
Softmax probabilities
    ↓
Top-k / Top-p filtering
    ↓
Next-token selection
```

The modules are independent and can be studied individually or in sequence. Each notebook isolates a specific LLM mechanism.

## Related project

This repository is a companion to [Building LLM](https://github.com/lucalullo/building-llm).

```text
Building LLM
→ build a language model progressively

Building LLM Technologies
→ isolate and understand the mechanisms used by LLMs
```

The first project focuses on evolution of a complete model. This project focuses on understanding individual technologies with minimal examples.

## Getting started

The notebooks are intentionally independent. You can follow them in order or open only the technology you want to review.

Most examples use standard Python. The calculations are deliberately small enough to inspect manually.

Start Jupyter:

```bash
jupyter notebook
```

Then open any version folder and run the notebook from top to bottom.

## Repository structure

Each technology has a self-contained version folder.

## Documentation

- [Project report (English)](project-report-en.pdf)
- [Relazione del progetto (Italiano)](project-report-it.pdf)
- [Project infographic](infographic.png)

## Limitations

- positional vectors are simplified to make the idea visible rather than reproduce sinusoidal encoding, learned production embeddings or RoPE;
- the multi-head notebook uses illustrative attention weights to show that different heads can focus differently; its final combination is a conceptual simplification rather than a complete learned Q/K/V and value-projection pipeline;
- Layer Normalization is reduced to mean/variance standardization and omits the small epsilon term and learned scale/shift parameters used in full implementations;
- the Transformer Block notebook focuses on the order and role of the sublayers; it is a data-flow sketch and does not reproduce every matrix operation already isolated in the Feed-Forward Network notebook;
- logits in the decoding notebooks are manually chosen to isolate softmax, temperature and filtering mechanisms;
- temperature is applied to logits before softmax;
- the top-k/top-p notebook demonstrates candidate filtering; a full sampler would normally renormalize the remaining probabilities and then sample from them.

## Project status

**The 10-version educational roadmap is complete.**

Future additions should only be made when a new mechanism can be explained with the same minimal, focused approach.

## License

Distributed under the [MIT License](LICENSE).

## Author

Created by [Luca Lullo](https://github.com/lucalullo).
