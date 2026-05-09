# 🌙 Intelligent Lunar Landing System

<p align="center">
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white">
  <img src="https://img.shields.io/badge/OpenAI_Gym-0081A5?style=flat-square&logo=openai&logoColor=white">
  <img src="https://img.shields.io/badge/BERT-FF6F00?style=flat-square&logo=google&logoColor=white">
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square">
</p>

> Fusing NLP embeddings with reinforcement learning to create an adaptive spacecraft controller — achieving **85–90% landing success** in simulated lunar descent.

---

## 🎯 What This Does

Traditional RL agents treat observations as pure numbers. This project fuses **BERT-encoded mission context** with a **Deep Q-Network (DQN)** to create an agent that adapts its landing strategy based on both physical state *and* natural language mission parameters (e.g., "minimize fuel", "hard surface detected", "emergency descent").

## 🔑 Key Results

| Metric | Result |
|---|---|
| Landing success rate | **85–90%** |
| Baseline DQN (no NLP) | ~72% |
| Training environment | OpenAI Gym LunarLander-v2 |
| Context encoding | BERT (bert-base-uncased, 768-dim) |

## 🧠 Architecture

```
Mission Context (text)
      │
   [BERT Encoder]
      │ 768-dim embedding
      │
Physical State (8-dim) ──→ [Concat] ──→ [DQN] ──→ Action
```

The BERT embedding is frozen and projected to 64-dim via a linear layer before concatenation with the physical state vector.

## 🛠️ Tech Stack

- **Framework**: PyTorch 2.x
- **RL Algorithm**: Deep Q-Learning with experience replay
- **NLP Backbone**: BERT (Hugging Face Transformers)
- **Environment**: OpenAI Gymnasium (LunarLander-v2)
- **Training**: Epsilon-greedy exploration, target network updates

## 🚀 Setup

```bash
git clone https://github.com/Aanshul3105/Lunar-Lander-using-NLP
cd Lunar-Lander-using-NLP
pip install torch gymnasium transformers numpy
python Lunar-Lander.py
```

## 📁 Files

| File | Purpose |
|---|---|
| `Lunar-Lander.py` | Main training + evaluation script |

## 💡 Why It's Interesting

Most RL research keeps language and control separate. This project explores early fusion — letting language semantics *directly* influence action selection, not just as a prompt. It's a small-scale prototype of architectures used in modern language-conditioned robotics (e.g., RT-2, SayCan).

---

*Part of my research into multi-modal RL at KIIT.*
