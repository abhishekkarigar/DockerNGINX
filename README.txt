run $ docker-machine ip
note down the ip and paste this ip in nginx.conf file in load-balancer/nginx.conf

before running the following command empty the contents of 
logs/nginx-access.log 
logs/nginx-error.log

$ docker-compose up -d --build
$ docker ps -a

exec into all the NodeJS containers in three different terminals

$ docker exec -it dockernginx_backend1_1 bash

	# node index.js
	
$ docker exec -it dockernginx_backend2_1 bash
	
	# node index.js
	
$ docker exec -it dockernginx_backend3_1 bash 

	# node index.js
	
	
curl <docker-machine ip>:8080   multiple times 

or go to browser

http://<docker-machine ip>:8080

refresh multiple times and observe the request being directed to all the servers in a 
round robin fashion.


to keep the logs even after the container is stopped 
$ docker-compose down

to remove the volumes also then 
$ docker-compose down --volumes
$ docker-compose down -v