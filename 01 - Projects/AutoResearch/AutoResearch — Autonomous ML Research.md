---
type: project
status: experimental
stack: Python, PyTorch, GPT, Muon optimizer
tags: [autoresearch, ml, ai, gpt, karpathy]
---

# AutoResearch — Autonomous ML Research

> Andrej Karpathy's autonomous AI research framework. An agent experiments with LLM pretraining configs overnight, modifying `train.py` and measuring `val_bpb`.

---

## 🔗 Connections

- **Author:** [[Andrej Karpathy]]
- **Related:** [[FinTra — Product (Mobile App)]] (shares no code — purely experimental)

---

## 📊 Tech Stack

| | |
|---|---|
| **Language** | Python 3.10 |
| **Deep Learning** | PyTorch 2.9.1 (CUDA 12.8) |
| **Attention** | Flash Attention 3 (`kernels`) |
| **Tokenizer** | rustbpe + tiktoken (custom BPE) |
| **Data** | climbmix-400b-shuffle (HuggingFace) |
| **Optimizer** | MuonAdamW (orthogonal momentum + AdamW) |
| **Package Mgr** | uv (Astral) |
| **Analysis** | Matplotlib, Pandas, Jupyter |

## 🧠 Architecture

- Custom GPT: RMSNorm, RoPE, Flash Attention 3, alternating sliding-window (SSSL), value embeddings (ResFormer), ReLU², per-layer residual scaling, logit softcapping
- ~50M params default (8 layers × 768 dim), single-GPU H100
- **5-minute wall clock budget** per experiment
- **BPB (bits-per-byte)** metric — vocab-size-independent
- **100% utilization dataloader** — best-fit document packing, BOS-aligned, zero padding
- Agent modifies `train.py`, runs 5-min experiments, keeps improvements, reverts regressions
- Logs to `results.tsv`

## 📄 Source

- **Path:** `/Users/dibyendumondal/Unicorns/original autoresearch/`
- **9 files** (excluding .venv)
- **Key files:** `train.py` (630 lines), `prepare.py` (389 lines), `program.md` (114 lines agent instructions)

---

## 📋 Related

- [[Andrej Karpathy]]