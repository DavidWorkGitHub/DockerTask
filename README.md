# DockerTask


Docker images are instances that are stored in containers. I've specified three services (nginx, wp, and db) in your provided Docker Compose file, and each service is linked to a Docker image. Docker will retrieve the designated images from Docker Hub (or another registry) and build containers based on those images when you execute the Docker Compose file.

You must take the following actions in order to place these images into containers:

Ascertain the installation of Docker and Docker Compose:
Ensure your system is configured with Docker and Docker Compose. These are available for download at https://docs.docker.com/get-docker/, the official Docker website.

Save your Docker Compose file: Save the file as docker-compose.yml or any other file ending in.yml.

Open the terminal and navigate to the directory where your Docker Compose file is located:
To find the directory containing your docker-compose.yml file, use the cd command.

Launch Docker Compose:
To activate the services listed in your Docker Compose file, execute the following command:

![Step one](https://github.com/DavidWorkGitHub/Docker-Task/assets/65865159/18d439a4-d727-4af9-bbaf-3c2bb4d6fb2d)

The containers are run in the background by the -d flag.

View Running Containers: The following can be used to see how your running containers are doing:

![tutorial 2](https://github.com/DavidWorkGitHub/Docker-Task/assets/65865159/dc1fbd61-eb4c-4a82-b222-aeb02ba50668)

You will see a list of all currently running containers with their names, IDs, and other details displayed when you run this command.

Your WordPress, MySQL, and Nginx containers ought to be operational at this point. Use your web browser to go to http://localhost to access your WordPress website.

Use the following command to halt and remove the containers:





Ensure Docker and Docker Compose are installed:
Make sure you have Docker and Docker Compose installed on your system. You can download them from the official Docker website: https://docs.docker.com/get-docker/

Save your Docker Compose file:
Save your Docker Compose file with a .yml extension, for example, docker-compose.yml.

Navigate to the directory containing your Docker Compose file in the terminal:
Use the cd command to navigate to the directory where your docker-compose.yml file is located.

Run Docker Compose:
Run the following command to start the services defined in your Docker Compose file
![Step one](https://github.com/DavidWorkGitHub/Docker-Task/assets/65865159/16e37ef6-b402-4de5-913c-aac98796451b)

![tutorial 3](https://github.com/DavidWorkGitHub/Docker-Task/assets/65865159/a4ba8010-5218-4d9f-8f00-a04d2bada3bd)


The containers specified in your Docker Compose file will be stopped and removed with this command.

Before deploying the configuration in a production environment, make sure it is tailored to your needs.


# Docker-Installation 
Installation of Docker and Docker Compose: Using the official instructions supplied by Docker, I started by installing Docker and Docker Compose on the target system.


Docker Compose File Creation: Carefully created, a docker-compose.yml file specifies how the Nginx, WordPress, and MySQL services should be configured. The required parameters—images, volumes, ports, and container names—are contained in this file.


Command Line Execution: I used the terminal to go to the directory where the docker-compose.yml file was located. To begin the creation and deployment of the Docker containers in detached mode, the docker-compose up -d command was run.


Verification of Running Containers: To confirm that the containers had been deployed successfully, the docker ps command was used. This command preserves the integrity of the environment by displaying an extensive list of all active containers.


Getting to the WordPress Website: To access the WordPress website, go to http://localhost in a web browser. This step verified that the Dockerized WordPress environment was operating correctly.
Container Termination: The docker-compose down command was run in the terminal to finish the deployment. In order to ensure a smooth shutdown of the Dockerized environment, this step gracefully stopped and removed the containers.


It turned out that the Dockerized WordPress environment was a successful and effective solution. Docker containers offer a reproducible and isolated environment, making deployment and maintenance simpler.



![Docker 1](https://github.com/DavidWorkGitHub/Docker-Task/assets/65865159/4104ea06-037f-40d4-a550-4c932f5465f6)


![Docker 2](https://github.com/DavidWorkGitHub/Docker-Task/assets/65865159/3f60198d-8ae9-472a-ae36-0b92ea9fdd36)


![Docker 3](https://github.com/DavidWorkGitHub/Docker-Task/assets/65865159/53f01f3d-2be2-4a80-bddb-af7d9eec3e3c)


![docker port](https://github.com/DavidWorkGitHub/Docker-Task/assets/65865159/b119666f-ee98-4889-bd72-ae29338d7f1a)




# Docker Compose

version: "3"
services:
  nginx: 
    image: nginx:latest
    restart: always
    container_name: production-nginx
    volumes:
      - /etc/letsencrypt/:/etc/letsencrypt/
      - ./nginx/:/etc/nginx/
      
    ports:
      - "80:80"
      - "443:443"
  wp:
    image: wordpress:latest
    restart: always
    container_name: production-wordpress
    environment:
      WORDPRESS_DB_HOST: production-db:3306
      WORDPRESS_DB_USER: dbuser
      WORDPRESS_DB_PASSWORD: dbpassword
      WORDPRESS_DB_NAME: wordpress
    volumes:
      - ./wordpress:/var/www/html
  db:
    image: mysql:5.7
    container_name: production-db
    restart: always
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_USER: dbuser
      MYSQL_PASSWORD: dbpassword
      MYSQL_RANDOM_ROOT_PASSWORD: "1"
    volumes:
      - ./mysql:/var/lib/mysql
