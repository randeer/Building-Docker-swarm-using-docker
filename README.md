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

![image](https://user-images.githubusercontent.com/39120946/202184276-8ab9b456-f810-47cf-aad8-1a948f0f95e7.png)


Navigate to http://192.168.99.100:888 to view Swarmpit web UI. Note, that you can use IP of any of the created nodes eg. address http://192.168.99.101:888 would work too. This is thanks to the ingress load-balancer running in you cluster by default.

------------------------------------
To acess this using web we can use the below browser docker image (https://hub.docker.com/r/jlesage/firefox)

docker run -d \
    --name=firefox \
    -p 5800:5800 \
    -v /docker/appdata/firefox:/config:rw \
    --shm-size 2g \
    jlesage/firefox
    
We need to run this command on host VM.

![image](https://user-images.githubusercontent.com/39120946/202180729-c9ed7195-d94b-4911-a8ea-28a36ce07de1.png)

![image](https://user-images.githubusercontent.com/39120946/202180075-b3141e72-0d9d-463c-a280-65a5d5158156.png)


---------------------------------------------------------------
Update a node as a worker or manager

docker node update --role manager node-3
