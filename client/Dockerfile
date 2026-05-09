FROM node:14 AS web_build

WORKDIR /usr/app

COPY ./ ./client

RUN cd client && npm install && npm run build --configuration production

FROM nginx:latest

RUN rm -rf /usr/share/nginx/html/*

COPY --from=web_build /usr/app/client/dist/client/ /usr/share/nginx/html/

COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]