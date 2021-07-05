FROM node:14-alpine

LABEL Description="GraphQL Portal Gateway" Vendor="GraphQL Portal"

#VOLUME ["/opt/graphql-portal"]
WORKDIR /opt/graphql-portal

#RUN wget https://raw.githubusercontent.com/GraphQL-Portal/graphql-portal-docker/main/config-examples/openshift/gateway/gateway.yaml -O /opt/graphql-portal/config/gateway.yaml
RUN mkdir ./config && cd ./config && wget https://raw.githubusercontent.com/GraphQL-Portal/graphql-portal-docker/main/config-examples/openshift/gateway/gateway.yaml
RUN ls -lha

RUN yarn global add @graphql-portal/gateway

ENV NODE_ENV production
EXPOSE 8080

CMD ["graphql-portal"]
