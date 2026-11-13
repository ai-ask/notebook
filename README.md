# Colab 一键推理脚本合集
收集 Google Colab 一键运行笔记本，搭配 cloudflared 隧道，对接 Cherry Studio 使用。

[![在 Colab 中打开](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ai-ask/colab/blob/main/qwen2.5-vllm.ipynb)

## 目录
- `ollama-qwen3.5-9b-v1.ipynb`
  主脚本：Ollama + cloudflared，Qwen3.5-9B + Qwen3-V1-8B
- `ollama-single.ipynb`
  轻量版，仅加载单个模型
- `ollama-ngrok.ipynb`
  备选隧道方案（ngrok）
- `ollama-debug.ipynb`
  端口、隧道排错调试脚本
- `qwen2.5-vllm.ipynb`
  vLLM + AWQ 量化 + cloudflared，支持工具调用，适合多并发访问

## 使用方法
1. 点击上方 Colab 徽章，打开笔记本
2. 运行时 → 更改运行时类型 → 硬件加速器选择 GPU（T4）
3. 依次执行全部单元格
4. 复制 cloudflared 公网地址，填入 Cherry Studio 的接口地址

## 实测说明
- Ollama GGUF：T4 上单聊速度 40～50 token/s，单用户聊天体验更好
- vLLM AWQ：携带 `--enforce-eager` 参数稳定性高，预热后稳定约 20 token/s；移除该参数速度上限更高，但首次提问会编译卡顿，CUDA 报错风险上升
