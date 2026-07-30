Entendo melhor a linha de comandos


## Instalando
Para buscar a image Docker do Ollama
```python
docker pull ollama/ollama:latest
```

Se tiver iniciado uma versão anterior
```python
docker stop ollama

```

Para remover a versão antiga. Mas talvez o melhor seja renomeá-la para usar depois. As novas versões Ollama podem ser problemas.

Para renomear com uma nova TAG que não seja mais latest.
```python
docker images
```
copie o IMAGE ID da linha com <none> ou outra <info>
REPOSITORY                      TAG                                   IMAGE ID       CREATED         SIZE
ollama/ollama                   latest                                dacbdaa86a43   3 days ago      4.76GB
metabase/metabase               <none>                                cffcebd4cd25   6 months ago    882MB
hello-world                     latest                                1b44b5a3e06a   11 months ago   10.1kB
ollama/ollama                   <none>                                fac4832afb0c   6 months ago    5.62GB

```python
docker tag <IMAGE_ID> ollama/ollama:0.15.2-backup

```
Para remover
```python
docker rm ollama

```
## Rodando

```python
docker run -d --gpus=all -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama:latest

```

explicando:
-d - roda em background
--gpus=all - permite usar todas as GPUs disponiveis. Pode ser uma específica.
-v - o volume a ser montado. Aqui vale a atenção. Dá para usar o mesmo volume com várias imagens diferentes. Por exemplo, usar um \
volume do servidor: /mnt/volume_ollama > -v /mnt/volume_ollama:/root/.ollama
-p - porta. Frequentemente um problema. O primeiro valor é a externo,o segundo é o interno, que é sempre 11434 (a menos que seja reconfigurado). por exemplo -p 11500:11434 permite usar a porta 11500
--name - é o nome da container que vai aparecer quando for executado. por exemplo --name ollama_versao1
no final do comando, a imagem a ser usada. Por exemplo, se tiver feito um TAG mencionado no começo, pode usar esse TAG para ativar a imagem.
