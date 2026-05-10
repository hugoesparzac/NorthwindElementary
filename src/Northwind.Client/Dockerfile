FROM node:22-alpine AS build
WORKDIR /app

COPY src/Northwind.Client/package*.json ./
RUN npm install

COPY src/Northwind.Client/ .

RUN npm run build

FROM nginx:alpine
WORKDIR /usr/share/nginx/html

RUN rm -rf ./*

COPY --from=build /app/dist/Northwind.Client/browser .

COPY src/Northwind.Client/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
ENTRYPOINT ["nginx", "-g", "daemon off;"]
