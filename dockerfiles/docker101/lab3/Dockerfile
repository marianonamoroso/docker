# LAB 3: Create an image with COPY instruction

# Create an image with COPY instruction
# COPY instruction in Multi-stage Builds

FROM nginx:alpine

COPY index.html /usr/share/nginx/html/

ENTRYPOINT ["nginx", "-g", "daemon off;"]
