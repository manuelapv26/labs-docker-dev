# Laboritorio 1 (Descargar imagenes)

# Se descargó imagen oficial de ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete 
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest

# Se descargó imagen de python:3.9
3.9: Pulling from library/python
ca4e5d672725: Pull complete 
30b93c12a9c9: Pull complete 
10d643a5fa82: Pull complete 
d6dc1019d793: Pull complete 
c387064957b7: Pull complete 
26766ebde481: Pull complete 
8a42d17fd0e2: Pull complete 
79eda865cc8a: Pull complete 
Digest: sha256:fea84f3a3b72c41efe7fc3b07ae209c6856b852b942c05fa88b747b74f70e711
Status: Downloaded newer image for python:3.9
docker.io/library/python:3.9

# laboratorio 1 (Ejecutar nuestro contenedor)
Ejecuto un contenedor de Nginx en segundo plano, mapeando el puerto 8080 del host al puerto 80 del contenedor:
627a94ba73a6e36f477559c0f59c2e6570406bdfb7626e9807db34c1e8d0789e

Ejecuto un contenedor de Ubuntu en modo interactivo:
root@8ee8f3479741:/# 

Ejecuto un servidor web Apache en segundo plano, mapeando el puerto 8000 del host al puerto 80 del contenedor
Unable to find image 'httpd:latest' locally
latest: Pulling from library/httpd
efc2b5ad9eec: Already exists 
fce1785eb819: Pull complete 
4f4fb700ef54: Pull complete 
f214daa0692f: Pull complete 
05383fd8b2b3: Pull complete 
88ad12232aa1: Pull complete 
Digest: sha256:932ac36fabe1d2103ed3edbe66224ed2afe0041b317bcdb6f5d9be63594f0030
Status: Downloaded newer image for httpd:latest
d6844eab2631ec826b803e50a084ff63df6d3204cdce17aed50a3dae71d52492

# Laboratorio 1 (Eliminar contenedores)
Eliminamos el contenedor de ubuntu: 
8ee8f3479741

visualizacion despues de eliminar ubuntu:

CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                                   NAMES
d6844eab2631   httpd     "httpd-foreground"       8 minutes ago    Up 8 minutes    0.0.0.0:8000->80/tcp, :::8000->80/tcp   beautiful_engelbart
627a94ba73a6   nginx     "/docker-entrypoint.…"   21 minutes ago   Up 21 minutes   0.0.0.0:8080->80/tcp, :::8080->80/tcp   charming_kepler

Eliminamos todos los contenedores detenidos:
@manuelapv26 ➜ /workspaces/labs-docker-dev (main) $ docker container prune -f
Total reclaimed space: 0B

solo se eliminan los que estan detenidos:
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                                   NAMES
d6844eab2631   httpd     "httpd-foreground"       12 minutes ago   Up 12 minutes   0.0.0.0:8000->80/tcp, :::8000->80/tcp   beautiful_engelbart
627a94ba73a6   nginx     "/docker-entrypoint.…"   25 minutes ago   Up 25 minutes   0.0.0.0:8080->80/tcp, :::8080->80/tcp   charming_kepler
