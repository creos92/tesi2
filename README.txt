Lato server:
Effettuare port forwarding della porta 1194 con l'IP LAN del pc che farà da server.
docker rm $(docker ps -a -q)
docker rmi $(docker images -q)

Da linea di comando:
su root 
xhost +local:root 
ip link delete tun* %eliminare tutte le interfacce tun (tun0,tun1)
svn checkout https://github.com/creos92/thesis.git/trunk/DockerfileServer
docker build DockerfileServer/ -t parloma:server
run -it --privileged --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" -p 1194:1194 parloma:server



Lato Client:
sudo ip link delete tun* %eliminare tutte le interfacce tun (tun0,tun1)
su root 
svn checkout https://github.com/creos92/thesis.git/trunk/DockerfileClient
docker build DockerfileClient/ -t parloma:client
docker run -it --privileged --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" parloma:client


Problemi:
Download del file
