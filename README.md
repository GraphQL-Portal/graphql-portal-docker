# GraphQL Portal Gateway and Dashboard Docker Builds

<p align="center">
    <img src="https://raw.githubusercontent.com/graphql-portal/graphql-portal-docker/main/graphql-portal.gif" />
</p>

[![from Paris with Love](https://img.shields.io/badge/from%20Paris%20with-%F0%9F%A4%8D-red)](https://shields.io/)

This repository contains various Docker Compose configurations for GraphQL Portal Gateway and Dashboard. 
Dockerfiles for Gateway and Dashboard are provided as separate containers in their respective repositories.

This repository also provides example configurations for different launch scenarios.

[Read more about GraphQL Portal Gateway and Dashboard in the official documentation](https://github.com/graphql-portal/graphql-portal#graphql-portal-gateway).

## Quickstart

The quickest way to start playing with the gateway is to pull this repository and use a docker-compose file to launch 
both the Gateway and the Dashboard:
```shell
git clone git@github.com:graphql-portal/graphql-portal-docker.git
cd graphql-portal-docker

docker-compose -f docker-compose.yml up
```

For more information, visit our [main repository with the documentation](https://github.com/graphql-portal/graphql-portal#quick-start).
