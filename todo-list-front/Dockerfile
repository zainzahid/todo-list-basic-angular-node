#Step 1
FROM node:12-alpine as build-step

WORKDIR /app

COPY package.json /app

RUN npm install

COPY . /app

RUN npm run build

RUN npm run test

# Step 2
FROM nginx:1.17.1-alpine

COPY --from=build-step app/dist/client /usr/share/nginx/html 