# Colab 一键推理脚本合集
Google Colab 一键推理笔记本，搭配 cloudflared 隧道，对接 Cherry Studio 使用。

[![Qwen2.5 vLLM](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ai-ask/colab/blob/main/qwen25-vllm.ipynb)
[![Ollama Qwen3.5](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ai-ask/colab/blob/main/ollama-qwen35.ipynb)

## 目录
- `ollama-qwen35.ipynb`
  Ollama + cloudflared，内置 Qwen3.5-9B、Qwen3-VL-8B，GGUF 量化，单用户速度快
- `qwen25-vllm.ipynb`
  vLLM + AWQ 量化 + cloudflared，支持工具调用，适合多并发访问

## 使用方法
1. 点击上方对应的 Colab 徽章，打开笔记本
2. 运行时 → 更改运行时类型 → 硬件加速器选择 GPU（T4）
3. 依次执行全部单元格
4. 复制 cloudflared 公网地址，填入 Cherry Studio 的接口地址

## 实测说明
- Ollama GGUF：T4 上单聊速度 40～50 token/s，单用户聊天体验更好
- vLLM AWQ：携带 `--enforce-eager` 参数稳定性高，预热后稳定约 20 token/s；移除该参数速度上限更高，但首次提问会编译卡顿，CUDA 报错风险上升
