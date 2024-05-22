### Listando Containers Docker (Todos)
~~~
docker ps –a
~~~
- **docker**: Comando para interagir com o Docker.
- **ps**: Subcomando para listar containers.
- **-a**: Flag para mostrar todos os containers, incluindo os parados.

### Removendo Todos os Containers Docker
~~~
docker rm $(docker ps -aq)
~~~
- **docker rm**: Subcomando para remover containers.
- **$(docker ps -aq)**: Comando entre parênteses executado primeiro. Ele exibe IDs de todos os containers em um único argumento (usando `-a` para incluir parados e `-q` para saída silenciosa).
- **$()**: Captura a saída do comando anterior e a utiliza como argumento para `docker rm`.

### Parando Todos os Containers Docker
~~~
docker stop $(docker ps -qa)
~~~
- **docker stop**: Subcomando para parar containers.
- A explicação é similar ao comando anterior, mas utilizando `docker stop` para parar os containers em vez de removê-los.

### Listando Containers Docker (Ativos)
~~~
docker container ls
~~~
**docker container ls**: Subcomando para listar containers ativos (executando).
### Listando Imagens Docker
~~~
docker image ls
~~~
**docker image ls**: Subcomando para listar imagens Docker disponíveis no sistema.

### Listando Volumes Docker
~~~
docker volume ls
~~~
**docker volume ls**: Subcomando para listar volumes Docker (armazenamento persistente).
### Limpando Volumes Docker Não Usados
~~~
docker volume prune
~~~
**docker volume prune**: Subcomando para remover volumes Docker que não estão associados a nenhum container.

### Listando Todos os Containers Docker (Incluindo Parados)
~~~
docker container -a
~~~
**docker container -a**: Subcomando para listar containers (equivalente a `docker ps -a`).


docker-compose up -d

docker-compose up --build

docker file

docker build . -t

docker stop $(docker ps -a -q)

docker rm $(docker ps -f status=exited -q)

docker ps -aq | xargs docker stop | xargs docker rm

docker rmi $(docker images -q)
