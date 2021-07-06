FROM node:14-alpine

LABEL Description="GraphQL Portal Dashboard" Vendor="GraphQL Portal"

WORKDIR /usr/app

# Install global packages
RUN yarn global add serve concurrently

RUN apk add git

# Copy all package.json files, including those from backend
RUN git clone https://github.com/graphql-portal/graphql-portal-dashboard ./

# Install packages
RUN yarn install --frozen-lockfile # --silent

ENV NODE_ENV production
ENV DASHBOARD_SECRET ""
ENV HOST localhost
ENV DASHBOARD_PORT 8008
ENV PUBLIC_HOST "http://localhost:8080"
ENV JWT_SECRET "defaultSecret"
ENV DEFAULT_ADMIN_EMAIL "admin@example.com"
ENV DEFAULT_ADMIN_PASSWORD "Secret123!"
ENV METRICS_ENABLED true
ENV CRYPTO_SECRET sMVzaYsaR9wM5R9cxLpJgjvqH9w6Ynlw
ENV REDIS_CONNECTION_STRING "redis://redis:6379"
ENV MONGODB_CONNECTION_STRING "mongodb://mongo:27017/graphql-portal-dashboard"
ENV REACT_APP_DASHBOARD_URL "http://localhost:8008/graphql"
ENV REACT_APP_DASHBOARD_WS_URL "$REACT_APP_DASHBOARD_URL"
ENV REACT_APP_DEFAULT_ADMIN_EMAIL "admin@example.com"
ENV REACT_APP_DEFAULT_ADMIN_PASSWORD "Secret123!"

# Build
COPY --chown=1001:0 ./ ./
RUN yarn build

EXPOSE 8008
EXPOSE 8080

ADD start.sh ./
RUN chmod +x ./start.sh

#RUN chgrp -R 0 /usr/app
RUN chmod g+w /usr/app

CMD ["./start.sh"]
