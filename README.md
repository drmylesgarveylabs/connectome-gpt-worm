[# 🪱 ConnectomeGPT-Worm

<p align="center">
  <i>A language model with a biological detour.</i>
</p>

<p align="center">
  Developed by <b>Dr. Myles Douglas Garvey</b> — Self-Funded AI Researcher<br>
  <a href="mailto:drmylesgarvey@gmail.com">drmylesgarvey@gmail.com</a>
</p>

<p align="center">
  <img src="model_representation.png" alt="ConnectomeGPT-Worm Architecture Diagram" width="800">
</p>

---

## 📌 Table of Contents

* [🧠 Overview](#-overview)
* [🏗️ Architecture](#️-architecture)

  * [Technical Specifications](#technical-specifications)
* [🧪 Experimental Matrix](#-experimental-matrix)

  * [🌐 Group A: Structural Integrity](#-group-a-structural-integrity)
  * [🔍 Group B: Ablations & Alterations](#-group-b-ablations--alterations)
* [📊 Evaluation & Benchmarks](#-evaluation--benchmarks)
* [💾 Dataset & Training Specs](#-dataset--training-specs)

  * [Hyperparameters](#hyperparameters)
* [⚠️ Limitations & Disclaimers](#️-limitations--disclaimers)
* [📜 Citation](#-citation)

---

## 🧠 Overview

**ConnectomeGPT-Worm** is an experimental GPT-style text model that embeds the actual biological neural circuitry of the roundworm (*C. elegans*) directly into its core architecture.

### The Core Question

> **Can 50 million years of biological evolutionary engineering serve as a useful inductive bias for next-token prediction?**

### The Mechanism

The model acts as a hybrid system, routing linguistic information through a **fixed biological network** before generating text.

### The Source

Neural synaptic weights were sourced directly from the **OpenWorm Project** GitHub repository.

---

## 🏗️ Architecture

A standard language model can be viewed as a largely continuous computational pipeline:

```text
Embeddings → Transformer → Next-Token Prediction
```

ConnectomeGPT-Worm introduces a biological detour into this pipeline:

```text
                    ┌─────────────────────┐
Language In ───────►│ Transformer Encoder │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Biological          │
                    │ Connectome          │
                    │                     │
                    │ 302 neurons         │
                    │ ~5,000 connections  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Transformer Decoder │
                    └──────────┬──────────┘
                               │
                               ▼
                         Language Out
```

The biological layer is not merely used as training data. It functions as an **architectural component of the model**, constraining the transformation of information between the encoder and decoder.

### Technical Specifications

| Component                     | Specification               |
| :---------------------------- | :-------------------------- |
| **Hidden Dimensions**         | 256                         |
| **Attention Heads**           | 4                           |
| **Context Window**            | 1,024 tokens                |
| **Biological Layer**          | 302 neurons                 |
| **Connectome Connectivity**   | ~5,000 connections          |
| **Connectome Initialization** | Biological synaptic weights |
| **Connectome Normalization**  | Largest eigenvalue = 1.0    |
| **Connectome Default State**  | Frozen                      |

The connectome matrix is normalized so that its largest eigenvalue is **1.0**, helping prevent unstable amplification or attenuation of signals as they propagate through the biological layer.

---

## 🧪 Experimental Matrix

Seven distinct configurations were tested across **5 independent random seeds** over **10,000 training steps**.

The experiments are designed to distinguish the contribution of:

* biological topology,
* biological synaptic weights,
* biological input/output pathways,
* network scale,
* trainability of the connectome,
* and the presence of the biological layer itself.

---

## 🌐 Group A: Structural Integrity

### Experiment 1 — The Real Thing (Fixed)

The actual *C. elegans* connectome is loaded and **frozen**.

The transformer must therefore learn to compute around the fixed biological constraints.

### Experiment 2 — Connectome Head Start (Trainable)

The connectome is initialized using biological synaptic weights but is subsequently allowed to adapt through backpropagation.

This tests whether the biological initialization provides a useful starting point even when the network is ultimately trainable.

### Experiment 3 — The Impostor (Random Weights)

The biological network's **sparsity and topology are preserved**, but its synaptic weights are randomized.

This separates the contribution of biological topology from the specific biological weight structure.

---

## 🔍 Group B: Ablations & Alterations

### Experiment 4 — Zooming Out (Subsets)

The connectome is reduced to increasingly smaller subsets of highly interconnected neurons.

Tested configurations:

* Top 50 neurons
* Top 100 neurons
* Top 200 neurons

This probes how model behavior changes as the biological network is scaled.

### Experiment 5 — Wrong Doors (Arbitrary I/O)

The biological connectome remains real and fixed, but the model bypasses the expected sensory/motor pathways and uses arbitrary entry and exit points.

Three configurations are tested:

* **5a — Arbitrary Inputs:** Inputs are randomized; outputs remain biological.
* **5b — Arbitrary Outputs:** Outputs are randomized; inputs remain biological.
* **5c — Both Randomized:** Both input and output pathways are randomized.

This tests whether the specific biological I/O organization contributes to model performance.

### Experiment 6 — Thawing the Worm (Phase 2)

Experiment 1 is first fully trained with the connectome frozen.

The transformer weights are then frozen, and **only the connectome is unfrozen** for an additional 10,000 surgical tuning steps.

This tests whether the biological layer itself can adapt to the linguistic task after the surrounding model has already learned.

### Experiment 7 — No Worm at All (Dense Baseline)

The biological connectome is removed entirely.

It is replaced with a standard, fully connected feedforward layer with equivalent parameter width.

This provides a direct baseline for determining whether the biological architecture provides an advantage over a conventional dense layer.

---

## 📊 Evaluation & Benchmarks

Models are evaluated every **50 training steps** using two core metrics.

### 1. Perplexity (PPL)

**Dataset:** WikiText-103

Lower perplexity indicates better next-token prediction performance.

Perplexity measures how uncertain the model is when predicting the next token in a sequence.

### 2. MMLU Accuracy

Models are evaluated across **8 academic subjects**, including:

* High School Biology
* College Biology
* Chemistry
* Physics
* Computer Science
* Abstract Algebra

The evaluation uses four-choice questions, giving a **25% random-guessing baseline**.

---

## 💾 Dataset & Training Specs

### Linguistic Data

**WikiText-103** is used as the primary language modeling dataset.

The dataset contains 100M+ tokens derived from featured Wikipedia articles and is tokenized using the GPT-2 tokenizer.

**Vocabulary size:** 50,257 tokens.

### Biological Data

The biological network is derived from the *C. elegans* hermaphrodite connectome.

The source data consists of an edge list containing chemical synaptic connections, with synaptic counts represented as edge weights.

Source:

**OpenWorm / CElegansNeuroML**

---

## Hyperparameters

| Parameter          | Value                                 |
| :----------------- | :------------------------------------ |
| **Hardware**       | 1 × NVIDIA A100 80GB                  |
| **Batch Size**     | 32 sequences × 1,024 tokens           |
| **Optimizer**      | AdamW                                 |
| **β₁**             | 0.9                                   |
| **β₂**             | 0.95                                  |
| **Weight Decay**   | 0.01                                  |
| **Learning Rate**  | 3 × 10⁻⁴                              |
| **LR Schedule**    | 500-step linear warmup → cosine decay |
| **Minimum LR**     | 10% of initial LR                     |
| **Precision**      | Native bfloat16                       |
| **Training Steps** | 10,000                                |
| **Random Seeds**   | 42, 123, 456, 789, 1337               |

---

## ⚠️ Limitations & Disclaimers

### Scale Threshold

At 256 hidden dimensions, this model operates well below the scale at which robust downstream reasoning typically emerges.

Consequently, small variations across random seeds may have substantial effects on MMLU performance.

### Domain Mismatch

The *C. elegans* nervous system evolved for biological functions such as:

* locomotion,
* chemotaxis,
* environmental sensing,
* feeding,
* and survival-related behavior.

It did not evolve to process human language.

Any benefit observed from the connectome therefore represents an **architectural effect**, rather than evidence that the biological network is inherently optimized for language.

### I/O Mapping Sensitivity

The model projects a continuous mathematical representation into a discrete set of biological neurons.

The choice of which neurons serve as input and output interfaces therefore introduces substantial architectural and experimental design assumptions.

---

## 📜 Citation

If you use this architecture, codebase, or biological mapping, please credit the original biological modeling work:

```bibtex
@article{gleeson2018c302,
  title={c302: a multiscale framework for modelling the nervous system of Caenorhabditis elegans},
  author={Gleeson, Padraig and others},
  journal={Philosophical Transactions of the Royal Society B: Biological Sciences},
  year={2018}
}
```

---

## 🔬 Project Status

This repository contains experimental research code and model configurations accompanying the ConnectomeGPT-Worm experiments.

Results should be interpreted as **exploratory experimental findings**, not as evidence that biological neural architectures are superior to conventional neural network architectures.

---

*Model card accompanying `worm_experiments_final_...ipynb`.*
](https://github.com/drmylesgarveylabs/connectome-gpt-worm)
