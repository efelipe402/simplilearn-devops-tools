# Testing docker swarm using alpine linux image

1. The docker compose yml it will pull and compile the image
2. The dockerfile will have all dependencies needed to be download and packaged into the image


# How to run it

Open 3 terminals and type:

1. docker compose up -d > inside the folder directory, the -f flag it will create the image for us.
2. docker run -it -v "/var/run/docker.sock:/var/run/docker.sock:rw" compose-manager-node-01:latest /bin/sh
3. docker run -it "/var/run/docker.sock:/var/run/docker.sock:rw" compose-worker-node-01:latest /bin/sh  
 > it will run the docker engine and create a bash terminal
4. Now let's create the swarm network, Inside the compose-manager-node-01's terminal type :
* ifconfig 
to get the machine ip 172.XXX or 192.XXX
* docker swarm init --advertise-addr 172.17.0.1
To initialize the swarm network 
* Copy the command shown at the terminal to join a worker node
docker swarm join --token SWMTKN-1-69z2dvbj55poese46gusauoamsex1rt765rfwgrsdj9ws2v6jh-c0e417yfbetejymd5hrrsp7gu 172.17.0.2:2377
* In the compose-worker-node-01's terminal type the command, that we just got from the output of the manager node, to join the network.
  

# NOTES:

The docker-compose has two part need to make docker swarm working

1. The compose-manager-node-01 will create and manage a network and will manage all request and task that will be done by a worker-node-01.
2. The worker-node-01 will connect to the compose-manager-node-01 network waiting to get any task sent from it.

# AT THE MOMENT THE CODE IS NOT ALLOWING COMPOSE-WORKER-NODE-01 TO BE ABLE AND CONNECT TO THE MANAGER HOST

