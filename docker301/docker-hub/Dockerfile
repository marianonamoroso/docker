FROM nginx:latest

COPY marianonamoroso.github.io/* /usr/share/nginx/html/

EXPOSE 80

ENTRYPOINT ["nginx", "-g", "daemon off;"]