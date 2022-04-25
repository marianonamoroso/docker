<img src="https://cdn.iconscout.com/icon/free/png-256/docker-2752207-2285024.png" width=100 height="100"/>
<h1>Docker</h1>
This repository contains helpful use commands and exercises for training Docker.<br><br>

<b>Exercises:</b><br> 

- https://dockerlabs.collabnix.com

<h2>Docker101</h2>

<h3>Getting Started with Docker Image</h3>

1. <b>Hello World Example</b>
      <details><summary>Show</summary>

      ```
      docker pull hello-world
      docker images
      ```
      ```
      docker run hello-world
      docker ps -a
      docker inspect <YOUR_CONTAINER_ID>
      ```
      </details>

2. <b>Working with Docker Images</b>
      <details><summary>Show</summary>

      ```
      docker images
      ```
      ```
      docker pull nginx
      docker images nginx # you can list only by name and tag (docker images nginx:latest)
      ```
      </details>

3. <b>Saving Images and Containers as Tar Files for Sharing</b>
      <details><summary>Show</summary>

      ```
      docker run -d -p 80:80 nginx
      docker ps
      ```
      ```
      docker export <YOUR_CONTAINER_ID> > nginx.tar
      docker import - importnginx < nginx.tar
      docker images # you can check the new image importnginx
      ```
      ```
      docker save -o savenginx.tar nginx
      ls -la
      ```
      ```
      docker rmi importnginx
      ```
      </details>

4. <b>How to build Your First Alpine Docker Image and Push it to DockerHub</b>
      <details><summary>Show</summary>

      ```
      docker run -d alpine sh
      ```
      ```
      docker exec -it <YOUR_CONTINAER_ID> sh # you can login into the container
      ```
      ```
      whoami
      cat /etc/*release
      apk update
      apk add git
      exit
      ```
      ```
      docker commit -m "GIT was added" <YOUR_CONTAINER_ID> agocho/alpine-git
      docker tag agocho/alpine-git:latest agocho/alpine-git:1.0
      docker images # you should see your new image called: agocho/alpine-git with the following tag: 1.0
      docker push agocho/alpine-git:1.0 # push your image in your personal docker account
      ```
      ```
      docker rmi <IDs> -f # you have to clean your environment (images)
      docker rm <IDs> -f # you have to clean your environment (containers)
      ```
      </details>

<h3>Accessing & Managing Docker Container</h3>

1. <b>Accessing the Container Shell</b>
      <details><summary>Show</summary>

      ```
      docker run -dit ubuntu
      docker images
      docker ps # you should see your ubuntu cotainer running 
      ```
      ```
      docker exec -it <YOUR_CONTAINER> bash
      exit
      ```
      ```
      docker attach <YOUR_CONTAINER> # you can also use, docker attach in order to connect to
      exit
      ```
      </details>
