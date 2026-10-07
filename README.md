# Free Local AI Coding Agent: 125B on a 16GB GPU (Strata + opencode)

▶️ Video: https://www.youtube.com/watch?v=QBPbvMaHkJc

📺 Part 1 (Strata on RTX 3090): https://github.com/network-tocoder/Run-a-125B-AI-Model-on-One-GPU-Strata-Qwen3.8-Flash-Next

A 125B mixture-of-experts model (Qwen3.8-Flash-Next, IQ3_S) running as a full coding agent on one **RTX 4060 Ti 16GB**, tested on 4 levels of real coding tasks. **$0 spent.**

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
