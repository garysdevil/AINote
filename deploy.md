# 概念
1. Ollama
    1. https://github.com/ollama/ollama
    2. https://ollama.com/
    3. 一个开源工具，主要功能是让用户能够在本地运行和管理大型语言模型（LLMs），无需依赖云服务。

2. open-webui
    1. https://github.com/open-webui/open-webui
    2. https://openwebui.com/
    3. 一个开源的、自托管的 AI 用户界面平台，主要用于与大型语言模型（LLMs）进行交互。


# 安装
## ollama
```sh
# Linux系统安装
curl -fsSL https://ollama.ai/install.sh | sh
# Mac系统安装
brew install ollama
# Windows系统直接去官网下载

# LLM默认存储路径 ~/.ollama
# windows系统通过环境变量设置路径 
    # set OLLAMA_MODELS=D:\AI\ollama 
    # setx OLLAMA_MODELS "D:\AI\ollama"
    # echo %OLLAMA_MODELS%

# 启动一个模型
# deepseek-r1:1.5b 模型占用1.1GB空间，至少 2GB 系统内存。
# deepseek-r1:671b 模型占用404GB空间，至少 40GB 系统内存。
# deepseek-r1:70b 模型占用43GB空间，至少 130GB 系统内存。
model=deepseek-r1:1.5b 
ollama run ${model}

# 启动 Ollama 服务
ollama serve
# 设置环境变量 OLLAMA_HOST 来指定服务地址
# export OLLAMA_HOST="0.0.0.0:11434"
```

```sh
# 使用
curl http://localhost:11434/api/generate -d '{
  "model": "deepseek-r1:1.5b",
  "prompt": "为什么天空是蓝色的？",
  "stream": false
}' | jq -r '.response'
```

## open-webui
```sh
# 使用docker启动
# 只安装 open-webui
docker run -d -p 3000:8080 --gpus=all --add-host=host.docker.internal:host-gateway -v /mnt/d/AI/open-webui_1:/app/backend/data --name open-webui_1 --restart always ghcr.io/open-webui/open-webui:main
# -e OLLAMA_BASE_URL=https://example.com # 使用非本地的LLM
# 访问 http://localhost:3000

# 安装绑定了ollama的 open-webui
docker run -d -p 3000:8080 --gpus=all -v /mnt/d/AI/ollama:/root/.ollama -v /mnt/d/AI/open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:ollama
# 访问 http://localhost:3000
```

```sh
# 使用pip启动
pip install open-webui
open-webui serve
# 访问 http://localhost:8080
```

## huggingface-cli
```cmd
REM 设置镜像
setx HF_ENDPOINT https://hf-mirror.com
echo %HF_ENDPOINT%
```
```sh
# 从huggingface下载模型参数 
# 下载中断后重新运行会继续从中段开始下载
huggingface-cli download Wan-AI/Wan2.1-T2V-14B --local-dir ./Wan2.1-T2V-14B
# --local-dir 保存在指定目录下
```

## Wan2.1
```powershell
# Define the prompt as a variable
$prompt = "Two anthropomorphic cats in comfy boxing gear and bright gloves fight intensely on a spotlighted stage."

# Use the variable in the Python command
python generate.py --save_file "D:\Dev\Wan2.1\2.1.mp4" --task t2v-1.3B --size 832*480 --ckpt_dir ./Wan2.1-T2V-1.3B --offload_model True --t5_cpu --sample_shift 8 --sample_guide_scale 6 --prompt "$prompt"
```

```log
# windows环境生成视频时指定输出文件名，否则报下面的错误 --save_file "D:\Dev\Wan2.1\2.mp4 
cache_video failed, error: result type Float can't be cast to the desired output type Byte
```