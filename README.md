# Building Docker Swarm Using Docker
Building a Dockerize enviroment

After installing docker.
We can configure using Docker dind.

docker run --privileged -d --name dind-test-1 -h node-1 docker:dind

Run it 3 times and create 3 nodes.
