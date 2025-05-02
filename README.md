# Containerized Nginx Server

This repository is a sample on how to run a Nginx server as a proxy in front of 3 applications servers to load balance and manage the connections to those servers.

Everything is done using Docker containers and Docker compose and you can run it locally without any effort, that is the beuty of Docker ;)

## How to run the server

It is very simple, just run the following command to spin up the server and the application servers all at once

```
docker compose -f docker/docker-compose.yaml up --build
```

The configrutation files are already mapped in the compose file. Just select the type of server you want to run (No SSL or with SSL).

If you run the server with SSL you have to create a `./nginx/certificates` folder and put in it the `.crt` and `.key` files in order to work.


## Useful commands for running the app

- docker image build -t nginx-app --file ./docker/Dockerfile .
- docker compose -f docker/docker-compose.yaml up --build
- docker exec -it docker-nginx-server-1 bash
- openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout nginx-selfsigned.key -out nginx-selfsigned.crt
- docker exec docker-nginx-server-1 nginx -s reload

## Acknowledgments

- This project was based on the [Tech With Nana video on Nginx](https://www.youtube.com/watch?v=q8OleYuqntY)