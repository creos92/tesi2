Da linea di comando:
Lato server:
su root 
xhost +local:root 
%ip link delete tun* %eliminare tutte le interfacce tun (tun0,tun1)
svn checkout https://github.com/creos92/thesis.git/trunk/DockerfileServer
docker build DockerfileServer/ -t parloma:server
run -it --privileged --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" -p 1194:1194 --name parloma:server parloma:server

Lato Client:
su root
%sudo ip link delete tun* %eliminare tutte le interfacce tun (tun0,tun1)
svn checkout https://github.com/creos92/thesis.git/trunk/DockerfileClient
docker build DockerfileClient/ -t parloma:client
docker run -it --privileged --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" --name parloma:client parloma:client


Problemi:
Download del file
docker rm $(docker ps -a -q)
docker rmi $(docker images -q)
