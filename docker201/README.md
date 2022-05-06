<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSyN4pyRe4qBnmt9dBZ9O-BwO8YJTw-pZ9sNcqNKD1r_pAcWoK2c2zUw5cEGwZtedc0om8&usqp=CAU" width=100 height="100"/>

<h2>Docker201</h2>

<h3>Docker Compose</h3>

1. <b>LAB 1: version</b>
      <details><summary>Show</summary>

      ```
      docker compose version
      ```
      </details>

2. <b>LAB 2: help</b>
      <details><summary>Show</summary>

      ```
      docker compose --help
      ```
      </details>

3. <b>LAB 3: config</b>
      <details><summary>Show</summary>

      ```
      docker compose config # validates the docker-compose.yml in the lab03 folder
      ```
      </details>

4. <b>LAB 4: build</b>
      <details><summary>Show</summary>

      ```
      docker compose build # you have to execute the cmd in the lab04 folder where our dockerfile and docker-compose.yml are located.
      ```
      </details>

5. <b>LAB 5: pull</b>
      <details><summary>Show</summary>

      ```
      docker-compose pull # you have to execute the cmd in the lab05 folder where our docker-compose.yml is located.
      ```
      </details>

6. <b>LAB 6: push</b>
      <details><summary>Show</summary>

      ```
      docker compose build # you have to execute the cmd in the lab06 folder where our dockerfiles and docker-compose.yml are located.
      ```
      ```
      docker images
      ```
      ```
      docker-compose push nginx_custom # you have to check your dockerhub repo
      ```
      </details>

7. <b>LAB 7: up</b>
      <details><summary>Show</summary>

      ```
      docker-compose up -d # you have to execute the cmd in the lab07 folder where our dockerfiles and docker-compose.yml are located.
      ```
      ```
      docker-compose ps
      ```
      </details>

8. <b>LAB 8: images</b>
      <details><summary>Show</summary>

      ```
      docker-compose up -d # you have to execute the cmd in the lab08 folder where our dockerfiles and docker-compose.yml are located.
      ```
      ```
      docker-compose images
      docker-compose ps
      ```
      </details>

9. <b>LAB 9: ps</b>
      <details><summary>Show</summary>

      ```
      docker-compose up -d # you have to execute the cmd in the lab09 folder where the docker-compose.yml is located.
      ```
      ```
      docker-compose images
      docker-compose ps
      docker-compose ps --services
      ```
      </details>

10. <b>LAB 10: stop</b>
      <details><summary>Show</summary>

      ```
      docker-compose ps
      ```
      ```
      docker-compose stop
      docker-compose ps # you should not see the containers
      ```
      </details>

11. <b>LAB 11: start</b>
      <details><summary>Show</summary>

      ```
      docker-compose start
      docker-compose ps
      ```
      </details>

12. <b>LAB 12: restart</b>
      <details><summary>Show</summary>

      ```
      docker-compose restart
      ```
      </details>