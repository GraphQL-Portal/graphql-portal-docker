FROM node:14-alpine

LABEL Description="GraphQL Portal Gateway" Vendor="GraphQL Portal"

WORKDIR /opt/graphql-portal

RUN mkdir ./config && cd ./config && wget https://raw.githubusercontent.com/GraphQL-Portal/graphql-portal-docker/main/config-examples/openshift/gateway/gateway.yaml

RUN yarn global add @graphql-portal/gateway

ENV NODE_ENV production
EXPOSE 8080

CMD ["graphql-portal"]
