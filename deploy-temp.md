```sh
brew install ollama
# 启动 Ollama 服务
ollama serve
# 设置环境变量 OLLAMA_HOST 来指定服务地址
# export OLLAMA_HOST="0.0.0.0:11434"
```
```sh
curl http://localhost:11434/api/generate -d '{
  "model": "deepseek-r1:1.5b",
  "prompt": "为什么天空是蓝色的？",
  "stream": false
}' | jq -r '.response'
```