# Notebook 一键推理脚本合集

本仓库存放 `.ipynb` GPU推理笔记本，适配 Google Colab、Kaggle Notebook 两个平台，脚本内置 cloudflared 隧道，生成公网地址，对接 Cherry Studio 使用。

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
- kaggle_llama_qwen3.6.ipynb：Kaggle专用｜LLMByAPPSTOY，Qwen3.6 / Llama 推理
> 💡 说明：脚本运行完成输出的cloudflared隧道地址，就是网页聊天地址，浏览器直接打开对话；
> 日志里会单独给出 OpenAI endpoint（自带 `/v1`），**直接复制这条带/v1的链接填入Cherry Studio**，不需要额外加 /api；
>
> API密钥用法：
> 本项目默认无鉴权，Cherry Studio密钥框不能留空，填写 `none` 作为占位即可。
>
> 📝 Kaggle 运行前置准备步骤（必须先做，再运行代码）
> 1. 打开笔记本，点击右侧【Input】，点【Add input】
> 2. 切换到【Datasets】标签，在搜索框输入：`tahsinekajolasalami`
> 3. 在搜索结果里勾选添加这两项：
>    - Qwen3.6-35B-A3B-DGUUF 模型文件
>    - llama-cpp-bin 依赖包
> 4. 点击上方【Settings】设置页面：
>    - ✅ 打开【Internet】（隧道联网开关，必须开启，否则cloudflared无法生成公网链接）
>    - Accelerator 加速器选项：把 `None` 修改为 `GPU T4 × 2`
> 5. 确认：脚本内的 username 相关参数你已经提前修改完成，无需再改动代码
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://github.com/ai-ask/notebook/blob/main/kaggle_llama_qwen3.6.ipynb)

## 使用说明
1. Kaggle 操作
   - ▶️ 运行：点击顶部 **双三角（Run all）** 图标，一次性全部单元格顺序执行
   - ⏹️ 停止：点击顶部 **停止方块图标**，终止任务，释放GPU、内存资源，避免持续消耗配额
2. Colab 操作
   - ▶️ 运行：点击顶部 **运行全部（Run all）**，批量执行所有单元格
   - ⏹️ 停止：点击顶部停止按钮终止会话，释放GPU资源；闲置不手动停止会持续占用Colab免费算力时长
3. 等待脚本执行，输出cloudflared隧道地址与API endpoint
4. Cherry Studio 分开新建服务：
   - Colab Ollama原生接口：地址不加 `/v1`，密钥填任意占位字符
   - Colab vLLM兼容接口：地址末尾带上 `/v1`，密钥填任意占位字符
   - Kaggle llama：直接复制日志中带 `/v1` 的endpoint；密钥填 `none` 占位
5. Kaggle脚本的隧道地址同时兼具【网页聊天】和【API调用】两种能力

## 配额说明
- Kaggle：提供**每月免费GPU配额**，配额用完当月无法再使用GPU加速；任务不手动停止、长时间挂机会持续消耗免费额度，用完只能等下个月重置。
- Colab：有免费算力时长限制，同样会消耗额度，长时间挂机、不停止会话会快速耗尽可用时长。

## 注意事项
1. Colab、Kaggle的GPU配额、时长限制互相独立
2. 脚本为前台常驻模式，关闭页面服务也可能继续跑，**用完一定要点停止按钮释放资源**
3. 不要把Colab脚本丢去Kaggle跑，反之亦然
4. `none` 只是Cherry Studio的占位文本，本后端默认不校验密钥
5. Kaggle互联网开关、加速器、数据集这三项配置缺一不可，缺一项会启动失败
