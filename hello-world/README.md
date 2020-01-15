Hello World with Docker using nginx alpine docker image
Pre-requisite
a. Install docker on your machine(this application is tested in window8.1 with Docker Tool)

Steps
Step 1: Create a Dockerfile
Filename: Dockerfile 



FROM nginx:alpine



# copy artifact build from the 'build environment'

COPY index.html /usr/share/nginx/html



# copy nginx configuration

#COPY ./nginx/nginx-default.conf /etc/nginx/conf.d/default.conf



# expose port 8080

EXPOSE 8080



# run nginx

CMD ["nginx", "-g", "daemon off;"] 

2. Create HTML file 
Filename: index.html



<!DOCTYPE html>

<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <meta http-equiv="X-UA-Compatible" content="ie=edge">

    <title>Hello World - Nginx Docker</title>

    <style>

        h1{

            font-weight:lighter;

            font-family: Arial, Helvetica, sans-serif;

        }

    </style>

</head>

<body>    

    <h1>

        Hello World

    </h1>

</body>

</html>

3.  The directory structure 
hello-world

    ─ Dockerfile

    ─ index.html

4. Create a Docker image
	docker build -t hello-nginx-alpine .

5. Create a Docker Container running this image
	docker stop hello-nginx-alpine

	docker rm hello-nginx-alpine

	docker run  -d -p 8080:80 --name hello-nginx-alpine  hello-nginx-alpine



	=============================

	ps : you can also use below command. This command will remove the container once it is

               stopped

	

	docker run --rm -it -p 8080:80 --name hello-nginx-alpine  hello-nginx-alpine



	--rm tells docker to remove the container once its stopped

	-it is used to attach interactive TTY

	-p 8080:80 is used to map the port 80 from the container to our computer port 8080

	-d will create a container with the process detached from our terminal

	-e is how you pass environment variables to the container  

	==========================

6. Open the browser of the host and run 
       http://localhost:8080

      ==========================

       ps: If you are running docker using "docker tool" on window 8.1then get host machine IP using

             below command then open the browser as below

       docker-machine ip  // 192.168.99.100



       http://192.168.99.100:8080 

       ==========================

Some Tips
8.  you can see docker container ports by running the docker port command.
	$ docker port hello-nginx-alpine

	80/tcp -> 0.0.0.0:8080

9.Go into container (work from power shell)	
       $ docker exec -it hello-nginx-alpine /bin/sh

      / #

======================================================================



Ref:

http://containertutorials.com/alpine/get_started.html

https://medium.com/myriatek/using-docker-to-run-a-simple-nginx-server-75a48d74500b

https://docs.docker.com/samples/

