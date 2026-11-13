# wellcaom colab
Personal collection of Google Colab notebooks.
Main focus: Ollama one-click inference with cloudflared tunnel, connect to Cherry Studio.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ai-ask/colab/blob/main/qwen2.5_vllm_ipynb.ipynb)

## Contents
- `ollama-qwen3.5-9b-vl.ipynb`
  Main script: Ollama + cloudflared, qwen3.5:9b + qwen3-vl:8b
- `ollama-single.ipynb`
  Lightweight version, single model
- `ollama-ngrok.ipynb`
  Alternative tunnel
- `ollama-debug.ipynb`
  Diagnostics for port & tunnel

## Usage
1. Click the badge above to open notebook in Colab
2. Runtime → Change runtime type → GPU (T4)
3. Run all cells
4. Copy the cloudflared public URL, paste into Cherry Studio Base URL

## Docs
- [Cherry Studio Config Guide](docs/cherry-studio.md)
- [FAQ](docs/faq.md)

## Notes
- Colab session will timeout automatically
- Cloudflared tunnel link changes on every restart
