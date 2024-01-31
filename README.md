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

![tutorial 3](https://github.com/DavidWorkGitHub/Docker-Task/assets/65865159/a4ba8010-5218-4d9f-8f00-a04d2bada3bd)


The containers specified in your Docker Compose file will be stopped and removed with this command.

Before deploying the configuration in a production environment, make sure it is tailored to your needs.
