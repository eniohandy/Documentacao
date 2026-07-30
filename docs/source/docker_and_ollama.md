Entendo melhor a linha de comandos

Para rodar um container/imagem Docker do Ollama

docker pull ollama/ollama:latest

docker stop ollama

docker rm ollama

docker run -d --gpus=all -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama:latest


