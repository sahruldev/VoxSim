# 🎙️ VoxSim – Zero‑Loss Multi‑Agent Sentiment Simulator

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

---

## 🖼️ Example Output

| PDF Report | Interaction Graph |
|------------|-------------------|
| *Professional report with structured sections* | *Directed graph showing who supports/opposes whom* |

*(Add screenshots of your actual output here)*

---

## 🚀 Quick Start (Google Colab)

Click the badge below to open the notebook:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yourusername/VoxSim/blob/main/VoxSim.ipynb)

Or run locally:

```bash
git clone https://github.com/yourusername/VoxSim.git
cd VoxSim
pip install -r requirements.txt
python voxsim.py