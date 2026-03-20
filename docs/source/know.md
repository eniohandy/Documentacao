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
