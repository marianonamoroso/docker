<img src="https://cdn.iconscout.com/icon/free/png-256/docker-2752207-2285024.png" width=100 height="100"/>

<h2>Docker101</h2>

<h3>Docker Image</h3>

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
      docker attach <YOUR_CONTAINER> # you can also use docker attach in order to connect to
      exit
      ```
      </details>

2. <b>Running a command inside running Container</b>
      <details><summary>Show</summary>

      ```
      docker run -dit ubuntu
      docker exec -it <YOUR_CONTAINER> bash
      exit
      ```
      </details>
      
3. <b>Managing Docker containers</b>
      <details><summary>Show</summary>

      ```
      docker rm -f $(docker ps -a -q) # you clean your desktop host
      ```
      ```
      docker run -d -p 8080:80 --name app1 nginx:latest
      docker run -d -p 8081:80 --name app2 nginx:latest
      docker ps
      ```
      ```
      docker stop app1 # you can stop your container named: app1
      docker kill app2 # you can kill your container named: app2
      docker ps -a # list all the containers (including non running containers)
      ```
      ```
      docker start app1 app2
      docker ps
      ```
      ```
      docker restart app2
      docker info
      docker top app1 # show the running process in the first container
      docker history nginx:latest
      ```
      ```
      docker inspect app1
      docker inspect app2
      ```
      ```
      docker logs app1
      docker logs app2
      ```
      </details>

<h3>Dockerfile</h3>

1. <b>LAB 1: IMAGE W/ GIT</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/alpine-git . # you have to go into the lab1 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker tag agocho/alpine-git agocho/alpine-git:1.1
      docker push agocho/alpine-git:1.1
      ```
      ```
      docker run -itd agocho/alpine-git:1.1 /bin/sh
      docker ps
      docker attach <YOUR_CONTAINER_ID>
      ```
      ```
      git --version
      exit
      ```
      </details>

2. <b>LAB 2: ADD</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/alpine-add . # you have to go into the lab2 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker tag agocho/alpine-add agocho/alpine-add:1.0
      ```
      ```
      docker run -itd agocho/alpine-add:1.0 /bin/sh
      docker ps
      docker attach <YOUR_CONTAINER_ID>
      ```
      ```
      ls -la pharosc_8.4.tar.gz
      exit
      ```
      </details>

3. <b>LAB 3: COPY</b>
      <details><summary>Show</summary>

      ```
      echo "Welcome to NGINX"  > index.html
      docker build -t agocho/nginx-copy . # you have to go into the lab3 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker run -d --name myapp1 -p 8080:80 agocho/nginx-copy
      ```
      ```
      curl localhost:8080
      ```
      </details>

4. <b>LAB 4: CMD</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/alpine-cmd . # you have to go into the lab4 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker run agocho/alpine-cmd # you should see the output of the CMD
      ```
      </details>

5. <b>LAB 5: ENTRYPOINT</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/alpine-entrypoint-exec . # you have to go into the lab5 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker run agocho/alpine-entrypoint-exec # you have to see the echo output configured
      ```
      ```
      vi Dockerfile # you have to comment the first ENTRYPOINT instruction
      docker run agocho/alpine-entrypoint-shell
      docker build -t agocho/alpine-entrypoint-shell .
      ```
      ```
      docker run --entrypoint "/bin/echo" agocho/alpine-entrypoint-exec "We are overriding the entrypoint instruction"
      ```
      ```
      docker rm $(docker ps -a -q)  
      docker rmi $(docker images -a -q)
      ```
      </details>

6. <b>LAB 6: WORKDIR</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/alpine-workdir . # you have to go into the lab6 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker run -it agocho/alpine-workdir sh # you have to see the echo output configured
      ```
      ```
      docker rm $(docker ps -a -q) -f 
      docker rmi $(docker images -a -q) -f 
      ```
      </details>

7. <b>LAB 7: RUN</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/alpine-run . # you have to go into the lab7 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker run -d -it agocho/alpine-run:latest
      ```
      ```
      docker history agocho/alpine-run:latest # you can check all the layers
      ```
      ```
      docker rm $(docker ps -a -q) -f 
      docker rmi $(docker images -a -q) -f 
      ```
      
      </details>
      
8. <b>LAB 8: ARG</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/alpine-arg . # you have to go into the lab8 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker build -t agocho/alpine-arg:1.0
      ```
      docker build -t agocho/alpine-arg:1.1 --build-arg command=whoami . # you can overrite the ARG param
      ```
      docker rm $(docker ps -a -q) -f 
      docker rmi $(docker images -a -q) -f 
      ```
      
      </details>

9. <b>LAB 9: ENV</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/alpine-env . # you have to go into the lab9 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker run agocho/alpine-env:latest
      ```
      ```
      docker run --env MESSAGE="We are testing imperative commands" agocho/alpine-env
      ```
      ```
      docker rm $(docker ps -aq) -f 
      docker rmi $(docker images -aq) -f 
      ```
      
      </details>

10. <b>LAB 10: VOLUME</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/nginx-vol . # you have to go into the lab10 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker run agocho/nginx-vol:latest
      docker volume ls
      docker inspect --format='{{.Mounts}}' <YOUR_CONTAINER_ID>
      ```
      ```
      docker rm $(docker ps -aq) -f 
      docker rmi $(docker images -aq) -f 
      ```
      
      </details>

11. <b>LAB 11: EXPOSE</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/nginx-expose . # you have to go into the lab11 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker run -d --rm -P --name nginx-8080 agocho/nginx-expose:latest
      ```
      ```
      docker run -d --rm -p 80:80 --name nginx-80 agocho/nginx-expose:latest # you can override the publish expose port
      ```
      ```
      docker rm $(docker ps -aq) -f 
      docker rmi $(docker images -aq) -f 
      ```
      
      </details>

12. <b>LAB 12: LABEL</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/nginx-label:1.0 . # you have to go into the lab12 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker run --rm -d --name nginx-label agocho/nginx-label:1.0
      ```
      ```
      docker inspect <YOUR_CONTAINER_ID> |grep -i labels -A2
      ```
      ```
      docker rm $(docker ps -aq) -f 
      docker rmi $(docker images -aq) -f 
      ```
      
      </details>

13. <b>LAB 13: ONBUILD</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/nginx-label:1.0 . # you have to go into the lab13 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker build -t agocho/busy-onbuild .
      ```
      ```
      docker build --file "DockerfileTrigger" -t agocho/busy-child-onbuild . # you should see the onbuild RUN ECHO
      ```
      ```
      docker rm $(docker ps -aq) -f 
      docker rmi $(docker images -aq) -f 
      ```
      
      </details>

14. <b>LAB 14: HEALTHCHECK</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/nginx-healthcheck . # you have to go into the lab14 folder and find the content of the Dockerfile
      ```
      ```
      docker run -d -P --name nginx-8080 agocho/nginx-healthcheck:latest
      ```
      ```
      docker logs <YOUR_CONTAINER> -f # you should see the following entry:  "GET / HTTP/1.1" 200 615 "-" "curl/7.74.0" "-"
      ```
      ```
      docker ps # you should see "healthy" in the STATUS section
      ```
      ```
      docker run -d --name nginx-80 -P --env NGINX_PORT=5000 agocho/nginx-healthcheck:latest
      docker ps # you should see "unhealthy" in the STATUS section because we override the curl port check to 5000
      ```
      ```
      docker rm $(docker ps -aq) -f 
      docker rmi $(docker images -aq) -f 
      ```
      
      </details>

15. <b>LAB 15: SHELL</b>
      <details><summary>Show</summary>

      ```
      docker buid -t agocho/windows-shell . # you have to go into the lab15 folder and find the content of the Dockerfile
      ```
      ```
      docker run agocho/windows-shell
      ```
      ```
      docker rm $(docker ps -aq) -f 
      docker rmi $(docker images -aq) -f 
      ```
      
      </details>

16. <b>LAB 16: ENTRYPOINT W/ RUN</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/busybox-entrypoint . # you have to go into the lab16 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker run --name entrypoint-cat-passwd agocho/busybox-entrypoint:latest
      ```
      ```
      docker run --name entrypoint-cat-shadow agocho/busybox-entrypoint:latest /etc/shadow # you can override the CMD
      ```
      ```
      docker rm $(docker ps -aq) -f 
      docker rmi $(docker images -aq) -f 
      ```
      
      </details>

17. <b>LAB 17: USER</b>
      <details><summary>Show</summary>

      ```
      docker build -t agocho/busybox-user . # you have to go into the lab17 folder and find the content of the Dockerfile
      ```
      ```
      docker images
      docker run -d --rm -it agocho/busybox-user
      ```
      ```
      docker exec <YOUR_CONTAINER_ID> id 
      ```
      ```
      docker rm $(docker ps -aq) -f 
      docker rmi $(docker images -aq) -f 
      ```
      
      </details>

<h3>Volumes</h3>

1. <b>Managing volumes through Docker CLI</b>
      <details><summary>Show</summary>

      ```
      docker volume create myvol
      docker volume ls
      docker inspect myvol
      ```
      ```
      docker volume rm myvol # docker volume rm $(docker volume ls -q)
      ```
      </details>

2. <b>Creating Volume Mount from docker run command & sharing same Volume Mounts among multiple containers</b>
      <details><summary>Show</summary>

      ```
      docker run -it -v my-volume:/data --name my-container-1 selaworkshops/busybox:latest
      cd /data/
      echo "volume" > volume.txt
      ```
      ```
      docker run -it -v my-volume:/data --name my-container-2 selaworkshops/busybox:latest
      cd /data/
      ls # you should see the volume.txt
      ```
      ```
      docker rm $(docker ps -a -q)
      ```
      ```
      docker run -it -v my-volume:/data --name my-container-3 selaworkshops/busybox:latest
      cd /data/
      ls # you should see the volume.txt
      ```
      ```
      docker rm $(docker ps -aq) -f 
      docker rmi $(docker images -aq) -f 
      docker volume rm $(docker volume ls -q)
      ```
      </details>

<h3>Networking</h3>

1. <b>LAB 1:</b>
      <details><summary>Show</summary>

      ```
      ```
      </details>