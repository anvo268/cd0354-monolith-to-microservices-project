### Build
FROM beevelop/ionic:v2021.04.1 AS ionic 
# Commenting out to use an earlier version: https://hub.docker.com/layers/beevelop/ionic/v2021.04.1/images/sha256-75eb48c20a851c2aeac7d40d55e36c3c4cc592f216b62097d979532e125302e0?context=explore
# FROM beevelop/ionic:latest AS ionic 
## Create app directory
WORKDIR /usr/src/app
## Install app dependencies
## A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
RUN npm ci
## Bundle app source
COPY . .
RUN ionic build
### Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html