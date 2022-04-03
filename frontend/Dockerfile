#STAGE 1
FROM node:16.14 AS build
WORKDIR /app
COPY package.json package-lock.json ./
COPY ssl-localhost/localhost.crt ./
COPY ssl-localhost/localhost.key /app/ssl
RUN npm install
COPY . .
RUN npm run build

#STAGE 2
FROM nginx:1.17.1-alpine

RUN mkdir -p /ssl
COPY --from=build /app/ssl/ /ssl/
ADD ssl-localhost/localhost.crt /etc/nginx
ADD ssl-localhost/localhost.key /etc/nginx

COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/dist/angular-ecommerce /usr/share/nginx/html

EXPOSE 80


