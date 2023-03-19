FROM node:alpine as builder
WORKDIR 'app'
COPY ./package.json ./
RUN nmp install
COPY . .
RUN nmp run build

FROM nginx
EXPOSE 3000
COPY ./ngix/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/ngix/html