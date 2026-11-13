# Notebook 一键推理脚本合集

本仓库存放 `.ipynb` GPU推理笔记本，适配 Google Colab、Kaggle Notebook 两个平台，脚本内置 cloudflared 隧道，生成公网API，对接 Cherry Studio 使用。

> 注意：文件后缀都是 `.ipynb`，但环境不一样，**不要跨平台混用脚本**
> ✅ 前缀 `colab_` → Colab打开运行
> ✅ 前缀 `kaggle_` → Kaggle打开运行

## 目录
### Google Colab
- colab_ollama_qwen3.5.ipynb：Ollama后端｜Qwen3.5 9B + Qwen3-VL 8B
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ai-ask/notebook/blob/main/colab_ollama_qwen3.5.ipynb)

- colab_qwen2.5_vllm.ipynb：vLLM后端｜Qwen2.5推理
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ai-ask/notebook/blob/main/colab_qwen2.5_vllm.ipynb)

### Kaggle Notebook
- kaggle_llama_qwen3.6.ipynb：Kaggle专用｜Llama / Qwen3.6推理
> 💡 说明：本脚本启动后会进入Llama UI网页后台，你可以在Llama UI后台设置里自定义API密钥，设置完成后，把隧道地址+密钥填入Cherry Studio即可对接。
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://github.com/ai-ask/notebook/blob/main/kaggle_llama_qwen3.6.ipynb)

## 使用说明
1. 点对应按钮跳转至对应平台
2. 运行单元格，等待输出cloudflared隧道地址
3. Cherry Studio 分开新建服务：
   - Ollama原生接口：地址不加 `/v1`
   - vLLM兼容接口：地址末尾带上 `/v1`
   - Kaggle Llama UI：在Llama UI后台配置API密钥，Cherry内填写对应隧道地址+你设置好的密钥
4. Colab侧Ollama / vLLM密钥填任意占位字符即可，默认不校验

## 注意事项
1. Colab、Kaggle的GPU配额、时长限制互相独立
2. 脚本为前台常驻模式，关闭页面服务就终止
3. 不要把Colab脚本丢去Kaggle跑，反之亦然
4. Kaggle这条的密钥**不是随便填**，必须和Llama UI后台里设置的密钥保持一致
