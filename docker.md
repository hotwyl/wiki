
docker-compose up -d

docker-compose up --build

docker file

docker build . -t

docker stop $(docker ps -a -q)

docker rm $(docker ps -f status=exited -q)

docker ps -aq | xargs docker stop | xargs docker rm

docker rmi $(docker images -q)
