# stage 1
FROM node:18-alpine AS builder

WORKDIR /app

COPY package.json ./

RUN npm install

COPY . .

RUN npm run build

# stage 2
FROM nginx:alpine

COPY nginx.conf /etc/nginx/conf.d/default.conf

COPY --from=builder /app/dist /usr/share/nginx/html

RUN rm -rf /var/cache/apk/* && \
    rm -rf /tmp/*

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]