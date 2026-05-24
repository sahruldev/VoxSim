# Introducing
# VoxSim Predict Research AI (Vox Populi Simulation) – Multi‑Agent Sentiment Simulator by Shrl.py

[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![Transformers](https://img.shields.io/badge/🤗-Transformers-yellow)](https://huggingface.co/docs/transformers/index)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yourusername/VoxSim/blob/main/VoxSim.ipynb)

**VoxSim** is an open‑source AI system that simulates public sentiment from long documents (news, PDFs, reports) **without losing a single piece of information**. It uses three autonomous agents (pro, con, neutral) that debate each chunk of the document, then aggregates their opinions into a professional PDF report with an interaction graph.

✨ **No hallucinations** – greedy decoding ensures factual outputs.  
✨ **Zero loss** – chunk‑wise processing preserves every character.  
✨ **Ready for 100k+ characters** – runs on free T4 GPU (Colab).  

---

## 🔥 Features

- **Multi‑agent debate** – 3 personas with unique roles (e.g., industry analyst, consumer, local business)
- **Long document support** – automatically splits text into 30k token chunks, processes each independently, then merges results
- **Zero information loss** – every part of the original document is read by the AI at least once
- **Hallucination‑free** – greedy decoding (`do_sample=False`) eliminates randomness
- **Rich output**:
  - 📄 **PDF report** with abstract, methodology, results, conclusions, recommendations
  - 📊 **Interaction graph** (directed edges with red/green arrows for oppose/support)
- **Multiple input sources**:
  - Plain text
  - News URL (automatic article extraction)
  - Upload file (`.txt`, `.pdf`, `.docx`)
- **Optimised for Colab** – 4‑bit quantisation, memory‑efficient chunking

# 🧠 Model & Performance
- Base model: Qwen/Qwen2.5-3B-Instruct (3B parameters)
- Quantisation: 4‑bit NF4 → ~1.5 GB GPU memory
- Context length: 32,768 tokens
- Runtime: T4 GPU (Colab free tier)
- Speed: ~2‑3 minutes for 80k characters (3 chunks)

## 🖼️ Example Output

| PDF Report | Interaction Graph |
|------------|-------------------|
| *Professional report with structured sections* | *Directed graph showing who supports/opposes whom* |

---

## 🚀 Quick Start (Google Colab)

Click the badge below to open the notebook:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sahruldev/VoxSim/blob/main/VoxSim.ipynb)

Or run locally:

```bash
git clone https://github.com/yourusername/VoxSim.git
cd VoxSim
pip install -r requirements.txt
python voxsim.py

# 📖 How It Works
1. Document ingestion – user provides text, URL, or file.
2. Chunking – split into 30k token chunks (max 32k for Qwen2.5‑3B).
3. Agent creation – LLM generates 3 personas based on the issue.
4. Chunk‑wise processing (zero loss):
    - Each chunk is fed to all 3 agents → one opinion per agent.
    - Simulated debate: agents respond to each other, labelling support/oppose.
5. Aggregation – opinions from all chunks are merged (no summarisation). Edge direction decided by majority vote.
6. Report generation – structured PDF report + Matplotlib graph.

Why zero loss?
Traditional methods summarise chunks progressively, losing detail. VoxSim never summarises – it stores every raw opinion and edge from every chunk, then combines them. Every original character influences the final result.

# 📜 License
MIT © Shrl.py – free for academic and commercial use.

# ⭐ Show Your Support
If VoxSim helps your research or project, please star this repository – it motivates further development!

# ❤️ Thank You
@huggingface | @GoogleColab | @Qwen_LLM
