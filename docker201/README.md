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

13. <b>LAB 13: pause</b>
      <details><summary>Show</summary>

      ```
      docker-compose pause
      docker-compose ps
      ```
      </details>

14. <b>LAB 14: unpause</b>
      <details><summary>Show</summary>

      ```
      docker-compose unpause
      docker-compose ps
      ```
      </details>

15. <b>LAB 15: logs</b>
      <details><summary>Show</summary>

      ```
      docker logs <YOUR_CONTAINER_ID> -f
      docker logs --tail="4" <YOUR_CONTAINER_ID>
      ```
      </details>

16. <b>LAB 16: port</b>
      <details><summary>Show</summary>

      ```
      docker-compose ps # you should apply the docker-compose.yml created in lab09 (docker-compose up -d)
      ```
      ```
      docker-compose port webserver 443 # you should see 0.0.0.0:443 
      docker-compose port webserver 80  # you should see 0.0.0.0:443 
      docker-compose port dbserver 5432 # you should see 0.0.0.0:5432 
      ```
      </details>

17. <b>LAB 17: run</b>
      <details><summary>Show</summary>

      ```
      docker-compose ps # you should apply the docker-compose.yml created in lab09 (docker-compose up -d)
      ```
      ```
      docker-compose run webserver /bin/sh
      ```
      </details>

18. <b>LAB 18: scale</b>
      <details><summary>Show</summary>

      ```
      docker-compose up -d # you have to execute the cmd in the lab18 folder where the docker-compose.yml is located.
      ```
      ```
      docker-compose ps --services
      ```
      ```
      docker-compose scale redis-slave=3
      docker-compose ps # you should see new three (3) replicas
      ```

      </details>

19. <b>LAB 19: exec</b>
      <details><summary>Show</summary>

   ```
      docker-compose ps # you should apply the docker-compose.yml created in lab09 (docker-compose up -d)
      ```
      ```
      docker-compose ps --services
      ```
      ```
      docker-compose exec webserver sh -c "echo 'EXEC: docker-compose exec execution' > /usr/share/nginx/html/index.html"
      ```
      ```
      curl http://localhost:80 # you should see the following text: EXEC: docker-compose exec execution
      ```

      </details>
      
20. <b>LAB 20: kill</b>
      <details><summary>Show</summary>

      ```
      docker-compose up -d # you have to execute the cmd in the lab18 folder where the docker-compose.yml is located.
      ```
      ```
      docker-compose kill # you kill the containers
      ```

      </details>

21. <b>LAB 21: rm</b>
      <details><summary>Show</summary>

      ```
      docker-compose up -d # you have to execute the cmd in the lab18 folder where the docker-compose.yml is located.
      ```
      ```
      docker-compose ps --services
      docker-compose stop webserver
      docker-compose rm # the container should be in the stopped state

      ```

      </details>

22. <b>LAB 22: down</b>
      <details><summary>Show</summary>

      ```
      docker-compose up -d # you have to execute the cmd in the lab18 folder where the docker-compose.yml is located.
      ```
      ```
      docker-compose down --rmi all
      docker-compose down --volumes
      ```
      ```
      docker images # you shouldn't see images
      docker ps # you shouldn't see containers
      ```

      </details>
      