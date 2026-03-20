#this is to give hints about the many problems that appear with Docker, Ollama and so on.


Sometimes start Ollama with docker gets stucked because it was started outside the Docker.
To check that, run:
‘systemctl status | grep ollama’ 
if the response is
├─ollama.service
           │ │ └─1949 /usr/local/bin/ollama serve
             │ │ └─742058 grep --color=auto ollama
you have to stop it with:

‘systemctl stop ollama.service’ para parar
