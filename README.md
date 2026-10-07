# Free Local AI Coding Agent: 125B on a 16GB GPU (Strata + opencode)

![GPU](https://img.shields.io/badge/Tested%20on-RTX%204060Ti%16GB-76b900?style=for-the-badge&logo=nvidia&logoColor=white)
![Model](https://img.shields.io/badge/Model-Qwen3.8--Flash--Next%20125B%20MoE-06b6d4?style=for-the-badge)
![Engine](https://img.shields.io/badge/Engine-Strata-f59e0b?style=for-the-badge)
![Cost](https://img.shields.io/badge/Cost-Free-brightgreen?style=for-the-badge)
![Cloud](https://img.shields.io/badge/Cloud-Not%20Required-red?style=for-the-badge)
![API](https://img.shields.io/badge/API-OpenAI%20Compatible-black?style=for-the-badge)

## 📺 The 125B-on-One-GPU Series

Run a **125B AI model locally** on a single consumer GPU with the free **Strata** engine. Every part is a real, hands-on test with configs and results.

| Part | Video | GPU | What you'll learn | Code |
|:---:|:---:|:---:|---|:---:|
| **1** | [![Part 1](https://img.youtube.com/vi/S5drxdKSE1s/mqdefault.jpg)](https://www.youtube.com/watch?v=S5drxdKSE1s)<br>[![Watch Now](https://img.shields.io/badge/YouTube-Watch%20Now-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/watch?v=S5drxdKSE1s) | **RTX 3090**<br>24GB | Run a 125B model on one GPU: Strata + Qwen 3.8 Flash-Next setup and first benchmarks | [![Repo](https://img.shields.io/badge/GitHub-Part%201-181717?style=for-the-badge&logo=github)](https://github.com/network-tocoder/Run-a-125B-AI-Model-on-One-GPU-Strata-Qwen3.8-Flash-Next) |
| **2** | [![Part 2](https://img.youtube.com/vi/QBPbvMaHkJc/mqdefault.jpg)](https://www.youtube.com/watch?v=QBPbvMaHkJc)<br>[![Watch Now](https://img.shields.io/badge/YouTube-Watch%20Now-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/watch?v=QBPbvMaHkJc) | **RTX 4060 Ti**<br>16GB | A free local AI coding agent: Strata + opencode through 4 coding levels and a racing-game boss | [![Repo](https://img.shields.io/badge/GitHub-Part%202-181717?style=for-the-badge&logo=github)](https://github.com/network-tocoder/free-local-ai-coding-agent-125b-on-16gb-gpu-strata-opencode) |
| **3** | [![Part 3](https://img.youtube.com/vi/c1DXLFLMRkk/mqdefault.jpg)](https://www.youtube.com/watch?v=c1DXLFLMRkk)<br>[![Watch Now](https://img.shields.io/badge/YouTube-Watch%20Now-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/watch?v=c1DXLFLMRkk) | **RTX 3080 Ti**<br>12GB | A new way to run Qwen 125B on 12GB V RAM: full setup, 75 tok/s writing, 2,035 tok/s reading, Pi 1.0 coding agent | [![Repo](https://img.shields.io/badge/GitHub-Part%203-181717?style=for-the-badge&logo=github)](https://github.com/network-tocoder/125B-Local-AI-on-a-12GB-GPU-Strata-Pi-1.0-Coding-Agent) |

### 🧭 Where should I start?
- **New to Strata?** Start with **[Part 1](https://www.youtube.com/watch?v=S5drxdKSE1s)** for the setup and the basics.
- **Want a local coding agent?** Jump to **[Part 2](https://www.youtube.com/watch?v=QBPbvMaHkJc)** (opencode).
- **Have only a 12GB GPU?** Go straight to **[Part 3](https://www.youtube.com/watch?v=c1DXLFLMRkk)** (Pi 1.0).

[![Subscribe](https://img.shields.io/badge/Subscribe-NetworkCoder-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@NetworkCoder?sub_confirmation=1)

⭐ If this helped, **star the repo** so more people can find it.

## Hardware
| Part | Spec |
|---|---|
| GPU | RTX 4060 Ti 16GB |
| CPU | Intel Core i5-11600K |
| RAM | 64 GB |
| Disk | NVMe SSD |

Strata loaded 46.84 GiB of experts in 28 s and cached **4,431 experts (8.45 GiB)** on the GPU (vs 8,752 on a 24GB RTX 3090).

## Results
| Level | Task | Time | Tests |
|---|---|---|---|
| 1 | Build a task manager app | 3m 38s | 5/5 ✅ |
| 2 | Fix a bug + add due dates | 4m 58s | 6/6 ✅ |
| 3 | Export/import + Docker + README | 3m 48s | 7/7 ✅ |
| Boss | Racing game (run 1, no budget) | 6m 35s | ❌ no code (thinking hit limit) |
| Boss | Racing game (run 2, budget 8000) | 4m 51s | ✅ game built |

- Write speed: **up to 52 tok/s** (~40–50 typical)
- Prompt read: **44K tokens in 1–3 s** (prefix reuse)
- Full data: [`results.csv`](results.csv)

## Setup
1. Install and start Strata (choose **64K context** on 16GB cards):
   ```
   ./setup.sh --port 8082
   ```
2. Install opencode: `npm install -g opencode-ai`
3. Copy [`config/opencode.json`](config/opencode.json) to `~/.config/opencode/opencode.json`
4. Run `opencode` in your project folder.

## The one setting: thinking budget
On big tasks the model can spend its whole output budget thinking. Add this to `strata-iq3_s.json` and restart Strata:
```json
"reasoning_budget_tokens": 8000
```

## Tips
- Set a thinking budget (~8000 tokens)
- Use 64K context on 16GB cards
- Start a fresh opencode session per project

## Which GPUs?
NVIDIA RTX 30-series or newer + 64 GB RAM. 24GB cards are the sweet spot; 16GB works (tested here); 12GB is untested.
