# GraphQL Portal Gateway and Dashboard Docker Builds

This repository contains various Docker Compose configurations for GraphQL Portal Gateway and Dashboard. 
Dockerfiles for Gateway and Dashboard are provided as separate containers in their respective repositories.

This repository also provides example configurations for different launch scenarios.

## Quickstart

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
