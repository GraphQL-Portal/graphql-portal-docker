# GraphQL Portal Gateway and Dashboard Docker Builds

![](graphql-portal.gif)

[![from Paris with Love](https://img.shields.io/badge/from%20Paris%20with-%F0%9F%A4%8D-red)](https://shields.io/)

This repository contains various Docker Compose configurations for GraphQL Portal Gateway and Dashboard. 
Dockerfiles for Gateway and Dashboard are provided as separate containers in their respective repositories.

This repository also provides example configurations for different launch scenarios.

[Read more about GraphQL Portal Gateway and Dashboard in the official documentation](https://github.com/code-store-platform/graphql-portal#graphql-portal-gateway).

## Quickstart

The quickest way to start playing with the gateway is to pull this repository and use a docker-compose file to launch both the Gateway and the Dashboard:
```shell
git clone git@github.com:code-store-platform/graphql-portal-docker.git
cd graphql-portal-docker

docker-compose -f docker-compose.yml up
```

## Standalone Gateway

```shell
docker pull gqlportal/gateway:latest
```

Now that you have Docker image locally, you will need to prepare a basic configuration file.
You may download a sample config from this repository:
```shell
curl -s -o ./gateway.yaml https://raw.githubusercontent.com/code-store-platform/graphql-portal-docker/main/basic.gateway.yaml
```

Once that is done, you can now launch the Gateway in a standalone mode:
```shell
docker run --name graphql-gateway \
  -p 3000:3000 \
  -v $(pwd)/gateway.yaml:/opt/graphql-portal/config/gateway.yaml
  gqlportal/gateway:latest
```

## Standalone Dashboard

```shell
docker pull gqlportal/dashboard:latest

docker run --name graphql-dashboard \
  -p 3030:3030 \
  gqlportal/dashboard:latest
```
