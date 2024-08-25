# Setup HAProxy as reverse proxy

The following guide provide sample for HAProxy configuration as reverse proxy on Docker container.

Three container will be created, two (2) back-end container running Apache httpd and one (1) front-end container running HAProxy. All containers runs on bridge network (172.19.0.0/16).

This guide assume that docker is running on host machine.

## How the site works

HTTP request to front-end container will be forwarded to two back-end containers in round-robin load balancing scenario.

```shell
curl http://localhost/
```

Back-end Apache httpd server can also be accessed by browser or curl

For container 1:

```shell
curl http://172.19.0.13:8080/
```

For container 2:

```shell
curl http://172.19.0.14:8080/
```

## Starting containers

To start up all containers:

```shell
docker-compose up -d
```

The site can be accessed by browser on port 80.

```shell
curl http://localhost/
```

## Stopping containers

To shut down all containers:

```shell
docker-compose down
```

## Container details

Details of the containers:

### Container 1

Service: Apache httpd
Bridge IP address: 172.19.0.13
Port: 8080

### Container 2

Service: Apache httpd
Bridge IP address: 172.19.0.14
Port: 8080

### Container 3

Service: NGINX
Bridge IP address: 172.19.0.12
Port: 80

