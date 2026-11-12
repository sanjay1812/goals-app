# Stage 1 compile react app
FROM node:14 AS stage

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

RUN npm run build

# Stage 2 publish to nginx

FROM nginx:alpine

COPY --from=stage /app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]


