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

# Laboratorio 2 (Crear un Dockerfile simple con Ubuntu y actualizar paquetes)

[+] Building 8.8s (6/6) FINISHED                                                                                                      docker:default
 => [internal] load build definition from dockerfile                                                                                            0.0s
 => => transferring dockerfile: 97B                                                                                                             0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                                0.0s
 => [internal] load .dockerignore                                                                                                               0.1s
 => => transferring context: 2B                                                                                                                 0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest                                                                                                  0.1s
 => [2/2] RUN apt-get update && apt-get upgrade -y                                                                                              7.6s
 => exporting to image                                                                                                                          0.6s
 => => exporting layers                                                                                                                         0.4s
 => => writing image sha256:afcc71d97f3cb1f4491594c2b33682793d29f865ffbf6e0cde3ba1065b2c2e79                                                    0.0s
 => => naming to docker.io/library/ubuntu-updated:latest 

 # Crear un Dockerfile para instalar Nginx en Ubuntu

[+] Building 13.9s (6/6) FINISHED                                                                                                     docker:default
 => [internal] load build definition from dockerfile                                                                                            0.1s
 => => transferring dockerfile: 138B                                                                                                            0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                                0.0s
 => [internal] load .dockerignore                                                                                                               0.0s
 => => transferring context: 2B                                                                                                                 0.0s
 => CACHED [1/2] FROM docker.io/library/ubuntu:latest                                                                                           0.0s
 => [2/2] RUN apt-get update && apt-get install -y nginx                                                                                       12.7s
 => exporting to image                                                                                                                          0.8s
 => => exporting layers                                                                                                                         0.7s
 => => writing image sha256:4f5a04c602bc174672b9a0eafc6fa9f8c00611499b1de9205b969ad5ee1b013d                                                    0.0s
 => => naming to docker.io/library/my-nginx:latest  

 # la aplicación se está ejecutando en el puerto 80
 de376f0f21d2a52a4d3a171333e33353f8b8153aa3b57f6f8ee7e33c2b8524ef

 # Modificamos el Dockerfile de Nginx para exponer el puerto 80
 [+] Building 0.5s (6/6) FINISHED                                                                                                      docker:default
 => [internal] load build definition from dockerfile                                                                                            0.1s
 => => transferring dockerfile: 148B                                                                                                            0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                                0.0s
 => [internal] load .dockerignore                                                                                                               0.1s
 => => transferring context: 2B                                                                                                                 0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest                                                                                                  0.0s
 => CACHED [2/2] RUN apt-get update && apt-get install -y nginx                                                                                 0.0s
 => exporting to image                                                                                                                          0.1s
 => => exporting layers                                                                                                                         0.0s
 => => writing image sha256:1d3984a11d2c324739d0220893f00b9fe057e375e345b4fb1d94618dbe255348                                                    0.0s
 => => naming to docker.io/library/my-nginx:latest 

 # Copiamos un archivo HTML local a una imagen de Nginx
[+] Building 2.3s (7/7) FINISHED                                                                                                      docker:default
 => [internal] load build definition from dockerfile                                                                                            0.1s
 => => transferring dockerfile: 94B                                                                                                             0.0s
 => [internal] load metadata for docker.io/library/nginx:latest                                                                                 0.0s
 => [internal] load .dockerignore                                                                                                               0.1s
 => => transferring context: 2B                                                                                                                 0.0s
 => [internal] load build context                                                                                                               0.2s
 => => transferring context: 255B                                                                                                               0.0s
 => [1/2] FROM docker.io/library/nginx:latest                                                                                                   0.8s
 => [2/2] COPY index.html /usr/share/nginx/html/                                                                                                0.2s
 => exporting to image                                                                                                                          0.7s
 => => exporting layers                                                                                                                         0.6s
 => => writing image sha256:a71f7998b05f1fb532eb6005a9854c9e03af50d94e45d93f6b080c44bac74016                                                    0.0s
 => => naming to docker.io/library/my-nginx:latest  

 # Usamos WORKDIR y copiamos un archivo
 [+] Building 2.1s (8/8) FINISHED                                                                                                      docker:default
 => [internal] load build definition from dockerfile                                                                                            0.0s
 => => transferring dockerfile: 87B                                                                                                             0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                                0.0s
 => [internal] load .dockerignore                                                                                                               0.0s
 => => transferring context: 2B                                                                                                                 0.0s
 => CACHED [1/3] FROM docker.io/library/ubuntu:latest                                                                                           0.0s
 => [internal] load build context                                                                                                               0.1s
 => => transferring context: 38B                                                                                                                0.0s
 => [2/3] WORKDIR /app                                                                                                                          0.2s
 => [3/3] COPY myfile.txt .                                                                                                                     0.3s
 => exporting to image                                                                                                                          1.2s
 => => exporting layers                                                                                                                         1.1s
 => => writing image sha256:c122ba3a622b9d9d4f87e032c9b28f3a4583d71a2c56b133824d61aa9be49489                                                    0.0s
 => => naming to docker.io/library/my-nginx:latest    

 # Ejecutamos un script Python al iniciar el contenedor
 [+] Building 3.8s (8/8) FINISHED                                                                                                      docker:default
 => [internal] load build definition from dockerfile                                                                                            0.1s
 => => transferring dockerfile: 111B                                                                                                            0.0s
 => [internal] load metadata for docker.io/library/python:3.9                                                                                   0.0s
 => [internal] load .dockerignore                                                                                                               0.0s
 => => transferring context: 2B                                                                                                                 0.0s
 => CACHED [1/3] FROM docker.io/library/python:3.9                                                                                              0.0s
 => [internal] load build context                                                                                                               0.1s
 => => transferring context: 30B                                                                                                                0.0s
 => [2/3] WORKDIR /app                                                                                                                          0.3s
 => [3/3] COPY script.py .                                                                                                                      0.3s
 => exporting to image                                                                                                                          2.7s
 => => exporting layers                                                                                                                         2.6s
 => => writing image sha256:04422fe5ba5a87269ab9976908f960c1580549b5aca3b537553f0d9aa13c7309                                                    0.0s
 => => naming to docker.io/library/python:3.9  