<img src="https://cdn.iconscout.com/icon/free/png-256/docker-2752207-2285024.png" width=100 height="100"/>
<h1>Docker</h1>
This repository contains helpful use commands and exercises for training Docker.<br><br>

<b>Exercises:</b><br> 

- https://dockerlabs.collabnix.com/

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