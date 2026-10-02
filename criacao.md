Docker - Manual para criação de containers, transferência para repositório, download em outro servidor e mais.

**Capítulo I - criação de Containers**

1. Criar container

Instalação do docker desktop

Se tiver a imagem instalada (“welcome to docker” p. ex.), executar. Ela vai pedir as opções. Preencher com a porta (8090, e.g.)

Acessar via localhost e porta.

PARA SABER EM QUE PORTA ESTÁ RESPONDENDO:

docker ps - aparece na coluna port

ou

docker port ID

1. Baixar uma imagem e fazer a imagem

para baixar, por exemplo:

git clone https://github.com/docker/welcome-to-docker

ir para a pasta da imagem.

Editar o arquivo Dockerfile e incluir o que mais quiser.

e.g.

# usa imagem bitnami mais enxuta debian

e instala utils que tem ping

FROM bitnami/minideb:latest

RUN apt-get update && apt-get install -y iputils-ping

depois, para compilar:

$ docker build -t my\_custom\_image . <= atenção ao ponto “.”; se não, não compila

para executar:

$ docker run -it my\_custom\_image

1. para mandar ao repositório e depois baixar e rodar em outro servidor:

Este primeiro comando coloca um tag na imagem. A maioria fica com o tag “latest”

docker tag my-image your-dockerhub-username/my-image:tag

Esse comando permite logar no Docker Hub.

docker login -u your-dockerhub-username

Se estiver usando o docker desktop, ele normalmente já está logado.

para mandar ao repositório.

docker push your-dockerhub-username/my-image:tag

Depois, no outro servidor, baixar:

docker pull your-dockerhub-username/my-image:tag

e rodar:

docker run [OPTIONS] your-dockerhub-username/my-image:tag

**Capítulo II - Gerando Container específicos**

A partir deste post do medium: [<u>Setting Up and Running Jupyter Notebook in a Docker Container | by bhavya sharma | Medium</u>](https://medium.com/%4018bhavyasharma/setting-up-and-running-jupyter-notebook-in-a-docker-container-d2acd713ce66)

Consegui criar uma imagem com jupyter notebook e ainda importei os pacotes da Holistic AI.

Um uma pasta criada, editar o arquivo Dockerfile. Incluir:

# Use an official Python runtime as a parent image

FROM python:3.8

# Set the working directory to /app

WORKDIR /app

# Install Jupyter Notebook

RUN pip install jupyter

# Make port 8888 available to the world outside this container

EXPOSE 8888

# Define environment variable

ENV NAME World

# Run Jupyter Notebook when the container launches

CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]

Se quiser, pode incluir a linha

# Install any needed packages specified in requirements.txt

RUN pip install --no-cache-dir -r requirements.txt

para o arquivo requirements. Lá eu coloquei os pacotes (pandas, seaborn, openai).

para construir:

docker build -t my-jupyter .

Dá para usar detalhes do comando do capítulo I.

Para executar:

docker run -it --mount type=volume,source=vol\_docker,target=/app/vol -p 8888:8888 imagem\_jupyter

obs:

1. o nome da imagem é aquele que foi usado. No caso, o nome certo é “my-jupyter”
2. o source do volume é o que existe na instalação. Em casa é diferente do trabalho

O detalhe aqui é que criei o volume chamado vol\_docker via docker desktop. Aí vc associa na hora de rodar. O volume fica acessível e pode guardar dados sem perder.

Quando se abrir a página de acesso (localhost:8888, [<u>p.ex</u>](http://p.ex).), na console aparece o token que tem que usar para logar.

**Capítulo III - Montando Volumes**

Algumas imagens já tem os volumes definidos, type=volume (como é o caso das que eu montei como imagens holistic AI

Mas pegando uma imagem sem volume, dá para:

docker run -d -it --name devtest --mount type=bind,source="C:\temp",target=/app my\_image

neste caso, o container montou uma imagem com a pasta C:\temp como /app. Isso fez com que os arquivos criados ficassem salvos na pasta temp do computador.

**Cap IV - Conectando a um Container**

docker container attach my\_image

crtl+p ou ctrl+q para desconectar sem parar o container. No teste que fiz, funcionou uma vez, outra não.

Para abrir um prompt bash:

docker exec -it <mycontainer> bash

**Cap V - Docker, Ollama e Webui**

[<u>How to use Ollama with Open WebUI with Docker and Docker Compose</u>](https://geshan.com.np/blog/2025/02/ollama-docker-compose/)

Esta receita funcionou.

Está no S11, na pasta test\_docker\_yml, o arquivo docker-compose.yaml

Ele junta o Ollama e o Webui.

a conta administrados é <u>enio.handy@gmail.com</u> e senha 12345678

Mas, não aparece a opção de baixar llms

dá para usar:

docker compose exec ollama ollama pull smollm2:135m

Aqui tb tem algumas info:

[<u>How to Connect Ollama to Open WebUI: User-Friendly Interface Setup | Markaicode</u>](https://markaicode.com/connect-ollama-open-webui-interface/#google_vignette)

[<u>Container Wonderland: Running Open-WebUI and Ollama Smoothly</u>](https://darknessnerd.github.io/2024/07/18/Container-Wonderland-Running-Open-WebUI-and-Ollama-Smoothly/)

![](data:image/png;base64...)

Aqui no site funcionando dentro do modelo **<u>compose</u>** dá pra baixar os modelos desde que se preencha com o nome

Com o Compose funcionando, há um log que fica na chamada, se não for invocado com -d para ficar em background.

Para ativar novamente o log, se cair:

docker logs -f open-webui
