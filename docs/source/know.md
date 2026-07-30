# Kwonledge Base

<!-- this page is to give hints about the many problems that appear with Docker, Ollama and so on. -->

# About Ollama

Sometimes start Ollama with docker gets stucked because it was started outside the Docker.
To check that, run:
```python 
systemctl status | grep ollama
```
if the response is
```python 
├─ollama.service
           │ │ └─1949 /usr/local/bin/ollama serve
             │ │ └─742058 grep --color=auto ollama
```
you have to stop it with:
```python 
systemctl stop ollama.service
```
para parar



no systemctl, se não resolver:

algum processo travado que ficou rodando que parece que não para p.ex. docker-35b0ff86a8c9d080d068c6fe32e807710cb2416bb1fc10b7b74df0f907630c50.scope
           │ │ └─432454 /bin/ollama serve

usando o início do identificador: 35b0ff86a8c9

docker stop <nome_ou_id>

docker rm <nome_ou_id>

Quando o container é removido, o dockerd automaticamente destrói a scope do systemd associada — ela não fica "solta" depois disso.

Se o docker stop não conseguir matar o processo

docker kill <nome_ou_id>
