# LAB 14: HEALTHCHECK

FROM nginx:latest

LABEL LAB="#14"

ENV NGINX_PORT=80

HEALTHCHECK --interval=30s --timeout=3s \
            CMD curl -f http://localhost:$NGINX_PORT || exit 1

EXPOSE 80