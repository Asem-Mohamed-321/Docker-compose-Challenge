# Rayagate Challenge

## steps:
 1. Creating the docker file for the php laravel api.
 2. Creating the docker files for the nuxt.js client.
 3. Creating a docker-compose.yml file in the root directory.
 4. Running the application using docker compose.
 5. tesiting the application.

## 1. Creating the docker file for the php laravel api:
  while creating the docker file I decided to use an ubuntu base image for my container after trying the composer and the php:8.1-fpm images due to the time limits of the challenge.
  
  I know it's not the most optimum approach but I was running out of time.

  <img src="https://github.com/user-attachments/assets/f940891f-0a41-4b55-9735-254349b280b7">

## 2. Creating the docker file for the Nuxt.js client:
  I used node:18-alpine as the base image to the container.

<img src="https://github.com/user-attachments/assets/002e15cf-06ad-409d-a314-ea32a243acb5">

## 3. Creating a docker-compose.yml file in the root directory:
  - Create a nginx.conf file in your directory and configure it to  act as a proxy forwarding requests to the Client ,because we will use this configuration file to the nginx service.
    <img src="https://github.com/user-attachments/assets/13848ee7-a4d4-4dd2-9ea2-984cba06ea64">

  - Created the docker-compose.yml file and specified the 4 services.
    take a look at the docker-composer.yml file in the repo.
    <img src="https://github.com/user-attachments/assets/82695524-78f4-4c3f-99e5-5bf6f75e49f3">

  
## 4. Running the application using docker compose:

 run the next commands to build the images used in the docker-compose.yml file and starting the running the containers
 ```
docker-compose build 
```

the output should look like this :
 <img src="https://github.com/user-attachments/assets/7c794a9d-5742-4921-9875-bed73d088470">

 note : you might encounter an error when migrating the database >> comment the migrate line in the docker file and do it manually after rntering the api container
 ```
docker exec -it <container name> bash

php artisan migrate
```

for deploying the containers use this command
```
docker-compose up -d
```

<img src="https://github.com/user-attachments/assets/b5a094d9-f14e-4f84-98c8-491c3fb9143e">

## 5. Testing the application:
 you can access the application using localhost:80/
 <img src="https://github.com/user-attachments/assets/c913eaac-fa12-48e7-b82d-6c0cdc6ee5b3">

 when you press "Add Book" it should write in the mysql database

*but this part doesn't work for me*

 using the next command you can access the mysql container 
 ```
docker exec -it <name of the container> mysql -u root -p
```
<img src="https://github.com/user-attachments/assets/1266ab2a-7323-4fd8-a4fd-35c7407dc1e8">


### You can also see the laravel welcome page indicates that the deployment process is complete 
<img src="https://github.com/user-attachments/assets/037652ce-67fc-4edd-9d8c-ed4c6ef15698">
