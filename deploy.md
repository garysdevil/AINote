# 概念
1. Ollama
    1. https://github.com/ollama/ollama
    2. https://ollama.com/
    3. 一个开源工具，主要功能是让用户能够在本地运行和管理大型语言模型（LLMs），无需依赖云服务。

2. open-webui
    1. https://github.com/open-webui/open-webui
    2. https://openwebui.com/
    3. 一个开源的、自托管的 AI 用户界面平台，主要用于与大型语言模型（LLMs）进行交互。


# 部署
```sh
# 安装
curl -fsSL https://ollama.ai/install.sh | sh
# 启动一个模型
model=llama3
ollama run ${model}
```
```sh
# 只安装 open-webui
docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
# --gpus all # 指定容器可以访问所有的 GPU 资源
# -e OLLAMA_BASE_URL=https://example.com # 使用非本地的LLM
# http://localhost:8080

# 安装绑定了ollama的 open-webui
docker run -d -p 3000:8080 --gpus=all -v ollama:/root/.ollama -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:ollama
# http://localhost:3000
```
```sh
pip install open-webui
open-webui serve
```