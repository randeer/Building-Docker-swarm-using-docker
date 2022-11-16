# Building a Docker Swarm Using Docker
Building a Dockerize enviroment

After installing docker.
We can configure using Docker dind.

docker run --privileged -d --name dind-test-1 -h node-1 docker:dind

Run it 3 times and create 3 nodes.

----------------------------------
To manage it we can use https://swarmpit.io/

Access one of manager node in swarm and run the below commands

docker run -it --rm \
  --name swarmpit-installer \
  --volume /var/run/docker.sock:/var/run/docker.sock \
swarmpit/install:1.9

Navigate to http://192.168.99.100:888 to view Swarmpit web UI. Note, that you can use IP of any of the created nodes eg. address http://192.168.99.101:888 would work too. This is thanks to the ingress load-balancer running in you cluster by default.

------------------------------------
Update a node as a worker or manager

docker node update --role manager node-3
