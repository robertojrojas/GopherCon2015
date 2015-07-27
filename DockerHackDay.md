# Command History of the Steps I followed at the Docker Hackday

docker info

docker version

docker images

docker run hello-world

docker images

docker pull busybox

docker run ubuntu:14.04 echo "Hello world"

docker run ubuntu:14.04 ps ax

docker run ubuntu:14.04 echo "Hello world"

time docker run ubuntu:14.04 ps ax

docker ps -a

docker run -d ubuntu:latest ping 127.0.0.1 -c 50

docker ps    # Get `<container id>` 

docker logs `<container id>` 

docker attach `<container id>` 

docker run -d --name docker-pinger ubuntu:latest ping 127.0.0.1 -c 50

docker logs docker-pinger

docker attach docker-pinger

docker rm docker-pinger # [ Remove it so you can run another container with the same name]

docker ps -qa   #[To display container ids only for all containers]

docker ps -a --filter "exited=1"

docker ps -a --filter "exited=0"

docker run -d -P nginx

docker ps # Get `<container name>`

docker attach `<container name>`

docker run -d nginx

docker ps 

exec -it `<container id>` bash

docker stop `<container id>` 

docker rm `<container id>` 

docker images

export PINGDOCKERID="`docker run -d ubuntu:14.04 ping 127.0.0.1 -c 100`"

docker logs $PINGDOCKERID

docker stop $PINGDOCKERID

docker start -a $PINGDOCKERID

docker ps # Since you exited from the terminal above no process should be running

docker start $PINGDOCKERID

docker images

docker inspect `<container id>`

docker images -a

docker ps -a # Get `<container name>`

docker inspect `<container name>` | more

docker inspect --format='{{.Config}}' $PINGDOCKERID

docker inspect --format='{{json .Config}}' $PINGDOCKERID


docker ps --filter='status=exited'

docker ps --help

docker run -i -t ubuntu:14.04 bash #[ run this echo "file data" > /tmp/newfile.txt ]

docker ps -a # Get first `<container id>`

commit `<container id>`
 
docker diff `<container id>`
 
docker commit `<container id>` <yourname>/ubuntu-new-file:1.0

docker images #[ You should see <yourname>/ubuntu-new-file:1.0 listed]
 
docker run -it <yourname>/ubuntu-new-file:1.0 bash #[ run cat /tmp/newfile.txt, echo "another change" >> /tmp/newfile.txt ]

docker ps -a # Get first `<container id>`

docker commit `<container id>` <yourname>/ubuntu-new-file:1.0.1

docker images

docker run -it robertojrojas/ubuntu-new-file:1.0.1 bash #[ run cat /tmp/newfile.txt]

mkdir docker-workshop

cd docker-workshop/

mkdir first-Image

cd first-Image/

vi Dockerfile

docker build .
