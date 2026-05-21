---
type: architecture
stack: Python, PyTorch, GPT
tags: [autoresearch, ml, architecture]
---

# AutoResearch Architecture

> Andrej Karpathy's autonomous ML research loop.

---

## 🔗 Connections

- **Author:** [[Andrej Karpathy]]
- **Project:** [[AutoResearch — Autonomous ML Research]]

---

## 📐 Experiment Loop

```
┌─────────────────────────────────────┐
│          PROGRAM.MD                 │
│  (Agent instructions, edited       │
│   by humans — the "controller")    │
└──────────────┬──────────────────────┘
               │
               ▼
┌─────────────────────────────────────┐
│          AI AGENT                    │
│  Reads program.md → modifies        │
│  train.py → runs experiment         │
└──────────────┬──────────────────────┘
               │
               ▼
┌─────────────────────────────────────┐
│     5-MINUTE TRAINING RUN          │
│  GPT model (~50M params)           │
│  MuonAdamW optimizer               │
│  measures val_bpb metric           │
└──────────────┬──────────────────────┘
               │
               ▼
┌─────────────────────────────────────┐
│     RESULTS.TSV                      │
│  val_bpb compared to baseline       │
│  Better? → keep changes             │
│  Worse?  → git revert               │
└─────────────────────────────────────┘
```

## 🧠 Model Details

- **Architecture:** Custom GPT with RMSNorm, RoPE, Flash Attention 3
- **Attention:** Alternating sliding-window (SSSL pattern)
- **Embeddings:** Value embeddings (ResFormer-style gated injection)
- **Activation:** ReLU²
- **Scaling:** Per-layer residual scaling (`resid_lambdas`, `x0_lambdas`)
- **Output:** Logit softcapping
- **Optimizer:** MuonAdamW — orthogonal momentum (Polar Express) for matrix params + AdamW for embedding/scalar params, per-shape LR scaling, cautious weight decay, Nesterov momentum

## 📊 Metrics

- **val_bpb** — validation bits per byte (vocab-size-independent)
- **Fixed 5-minute wall clock budget** per experiment

---

## 📋 Related

- [[AutoResearch — Autonomous ML Research]]
- [[Andrej Karpathy]]