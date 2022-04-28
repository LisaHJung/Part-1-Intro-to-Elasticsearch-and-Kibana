Related Resource
- [docker-compose.yml](https://github.com/LisaHJung/Part-1-Intro-to-Elasticsearch-and-Kibana/blob/main/docker-compose.yml)

For this Beginner's Crash Course, you can also use Docker to run Elasticsearch and Kibana this is not showed in the youtube video but it is optional and another popular way to install the software. You're going to find a docker-compose file that is going to deploy and install both Docker images using the following version.

- elasticsearch:7.11.1
- kibana:7.11.1

In order to be able to run this, you will need to have installed:

- [Docker](https://docs.docker.com/desktop/linux/) or  [Docker Desktop](https://docs.docker.com/desktop/).
- [Docker Compose](https://docs.docker.com/compose/).

Install Elasticsearch and Kibana by using the following command:

```sh
docker-compose up -d
```

The previous command is going to spin up two docker containers that will be in the same Docker network and in detached mode. With this, you will be able to open the following urls :

* http://localhost:5601/ - Kibana Web UI interface
* http://localhost:9200/ - Elastic Search API

If you want to check the logs :
```sh
docker-compose logs elasticsearch
```
for Kibana :
```sh
docker-compose logs kibana
```
If you want to stop Elasticsearch and Kibana, you will need to run the following command :
```sh
docker-compose stop
```
If you want to stop and destroy the docker services :

```sh
docker-compose down
```
