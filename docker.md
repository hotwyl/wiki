## Docker Compose and Docker Commands

This document outlines essential commands for working with Docker Compose and Docker.

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

### Docker Compose

* **`docker-compose up -d`**
  - Esse comando inicia todos os serviços definidos no seu arquivo`docker-compose.yml` em modo detached (segundo plano). Isso permite que os serviços rodem em segundo plano sem a necessidade de manter o terminal aberto.
    
* **`docker-compose up --build`**
  - Este comando constrói as imagens Docker para seus serviços com base nos Dockerfiles em seu diretório de projeto (se ainda não tiverem sido construídas) e, em seguida, inicia os serviços.

### Docker

* **`docker file`** (**Comando Incorreto**)
  - Não existe um comando Docker integrado chamado `docker file`. É provável que você tenha se referido a um Dockerfile, que é um arquivo de texto contendo instruções para construir uma imagem Docker. Você não pode executar um Dockerfile diretamente usando um comando Docker.

* **`docker build . -t <image_name>`**
  - Este comando constrói uma imagem Docker a partir do Dockerfile no diretório atual e a marca com o `<image_name>` especificado.

* **Gerenciando Containers**

  Parar e Remover Containers:

  * **`docker stop $(docker ps -a -q)`**
    - Para todos os containers em execução (incluindo os detached).
    - `docker ps -a -q` lista todos os containers (em execução e parados) no modo silencioso (apenas IDs de container).
    - A saída é canalizada (`|`) para `docker stop` para parar cada container.

  * **`docker rm $(docker ps -f status=exited -q)`**
    - Remove todos os containers encerrados.
    - `docker ps -f status=exited -q` lista apenas containers encerrados no modo silencioso.
    - A saída é canalizada para `docker rm` para remover cada container encerrado.

  * **`docker ps -aq | xargs docker stop | xargs docker rm`** (**Abordagem Alternativa**)
    - Uma maneira alternativa de alcançar o mesmo resultado que os dois comandos anteriores combinados.
    - `docker ps -aq` lista todos os IDs de container no modo silencioso.
    - `xargs docker stop` para cada container listado na saída do comando anterior.
    - `xargs docker rm` remove cada container parado.

**Remover Imagens:**

* **`docker rmi $(docker images -q)`** (**Cuidado Aconselhado**)
  - Remove todas as imagens Docker do seu sistema.
  - **Use este comando com cautela!** Ele removerá todas as imagens, incluindo aquelas que podem ser usadas por outros projetos. Considere usar `docker rmi <image_name>` para remover imagens específicas.

**Observações Adicionais:**

* Certifique-se de ter o Docker instalado e em execução antes de usar esses comandos.
* Consulte a documentação oficial do Docker para obter informações detalhadas sobre cada comando e suas opções: https://docs.docker.com/
