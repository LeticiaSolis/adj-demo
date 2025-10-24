FROM node:20 AS build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

ARG API_HOST 
ARG API_PORT 
ARG API_BASE 

ENV VITE_API_HOST
ENV VITE_API_PORT 
ENV VITE_API_BASE 

RUN npm run build
 
FROM nginxalpine

COPY --frombuild /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "demo off;"]