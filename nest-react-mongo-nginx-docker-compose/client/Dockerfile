# build
FROM node:13.12.0-alpine as build
WORKDIR /app
COPY . .
RUN npm install
RUN npm run-script build

# prod
FROM nginx:stable-alpine

RUN apk add --update nginx && rm -rf /var/cache/apk/*

COPY config/nginx.conf /etc/nginx/nginx.conf
COPY config/vhost.conf /etc/nginx/conf.d/vhost.conf
COPY --from=build /app/public public

# forward request and error logs to docker log collector
RUN ln -svf /dev/stdout /var/log/nginx/access.log \ && ln -svf /dev/stderr /var/log/nginx/error.log

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]

