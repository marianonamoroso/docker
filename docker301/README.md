<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSyN4pyRe4qBnmt9dBZ9O-BwO8YJTw-pZ9sNcqNKD1r_pAcWoK2c2zUw5cEGwZtedc0om8&usqp=CAU" width=100 height="100"/>

<h2>Docker301</h2>

<h3>Docker Content Trust</h3>

1. <b>LAB 1: pull</b>
      <details><summary>Show</summary>

      ```
      docker pull nginx:latest
      docker images
      ```
      ```
      docker run -d nginx:latest
      docker ps
      ```
      </details>

2. <b>LAB 2: pull (digest)</b>
      <details><summary>Show</summary>

      ```
      docker pull nginx:latest
      docker pull nginx@sha256:8f3ae197551a12be41805c33e60e4ced1089d1cfc6f31516107e733d5b2b08ac
      docker images # you should see two nginx images
      ```
      ```
      docker run -d nginx:latest
      docker ps
      ```
      </details>

<h3>Docker Secrets Management</h3>

1. <b>LAB 1: create a secret</b>
      <details><summary>Show</summary>

      ```
      docker secret create secret-1 secrets/sec.txt
      ```
      </details>

2. <b>LAB 2: manage secrets</b>
      <details><summary>Show</summary>

      ```
      docker secret ls
      ```
      </details>
      
3. <b>LAB 3: access secrets</b>
      <details><summary>Show</summary>

      ```
      docker service create --name service-secret --secret="secret-1" redis:alpine
      ```
      ```
      docker service inspect service-secret
      ```
      ```
      docker service ps service-secret
      docker exec -it <YOUR_CONTAINER_ID> sh
      ```
      ```
      ls -l /run/secrets
      cat /run/secrets/secret-1
      ```
      ```
      docker secret rm $(docker secret ls -q)
      ```
      </details>

<h3>Security Scanning with Docker Hub</h3>

1. <b>LAB 1: docker-hub</b>
      You have to create a new private repo and enable the vulnerability scanning.

2. <b>LAB 2: docker-hub and create the image</b>
      <details><summary>Show</summary>

      ```
      docker build -t website . # you have to go into the docker-hub folder and find the content of the Dockerfile
      ```
      </details>

3. <b>LAB 3: tag</b>
      <details><summary>Show</summary>

      ```
      docker images
      docker image tag website:latest agocho/website:scan # you have to replace "agocho" with your account name
      docker images # you should see two images (tag: latest/scan)
      ```
      </details>

4. <b>LAB 4: push</b>
      <details><summary>Show</summary>

      ```
      docker push agocho/website:scan  # you have to replace "agocho" with your account name
      ```
      </details>

5. <b>LAB 5: scan</b>
      You should see the scan results 


      