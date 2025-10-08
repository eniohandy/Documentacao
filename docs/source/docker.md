# Docker - Manual para criação de containers, transferência para repositório, download em outro servidor e mais.

## Capítulo I - Criação de Containers


Criar container


Instalação do docker desktop

Se tiver a imagem instalada (“welcome to docker” p. ex.), executar. Ela vai pedir as opções. Preencher com a porta (8090, e.g.)

Acessar via localhost e porta.

PARA SABER EM QUE PORTA ESTÁ RESPONDENDO:

docker ps - aparece na coluna port
ou
docker port ID


Baixar uma imagem e fazer a imagem

para baixar, por exemplo:

git clone https://github.com/docker/welcome-to-docker


ir para a pasta da imagem.

Editar o arquivo Dockerfile e incluir o que mais quiser.

e.g.

# usa imagem bitnami mais enxuta debian
e instala utils que tem ping
FROM  bitnami/minideb:latest
RUN apt-get update && apt-get install -y iputils-ping

depois, para compilar:
$ docker build -t my_custom_image .    <= atenção ao ponto “.”; se não, não compila

para executar:
$ docker run -it my_custom_image

para mandar ao repositório e depois baixar e rodar em outro servidor:
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




## Capítulo II - Gerando Container específicos


A partir deste post do medium: Setting Up and Running Jupyter Notebook in a Docker Container | by bhavya sharma | Medium

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

docker run -it --mount type=volume,source=vol_docker,target=/app/vol -p 8888:8888 imagem_jupyter

obs:
o nome da imagem é aquele que foi usado. No caso, o nome certo é “my-jupyter”
o source do volume é o que existe na instalação. Em casa é diferente do trabalho


O detalhe aqui é que criei o volume chamado vol_docker via docker desktop. Aí vc associa na hora de rodar. O volume fica acessível e pode guardar dados sem perder.

Quando se abrir a página de acesso (localhost:8888, p.ex.), na console aparece o token que tem que usar para logar.
