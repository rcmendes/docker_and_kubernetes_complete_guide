# FROM node:12-alpine as builder
FROM node:12-alpine

WORKDIR /app

COPY package.json .
RUN npm install

COPY src ./src
COPY public ./public

RUN npm run build

# Nginx
FROM nginx:1.19-alpine
COPY --from=0 /app/build /usr/share/nginx/html
# COPY --from=builder /app/build /usr/share/nginx/html