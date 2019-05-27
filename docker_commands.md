# Docker Course 

https://farfetch.udemy.com/docker-and-kubernetes-the-complete-guide

# Commands reference

- #### Create and start a container
        $> docker run <image> <override command>

- #### Show all running containers
        $> docker ps

- #### Show running and stopped containers
        $> docker ps -a

- #### Remove a stopped container
        $>  docker rm <container_id> 

- ####  Remove the image
        $>  docker rmi <image_id>

- ####  Remove all the stopped container all the build cache
        $>  docker system prune 

- ####  Get all logs from the container
        $>  docker logs <container_id>

- ####  Get all logs from the container but keep follow the logs 
        $> docker logs <container_id>  -f

- ####  Stop the container. A SIGTERM message will be fired to terminate your container, this way you have some seconds and can watch the SIGTERM signal to do something when a container is terminated
        $> docker stop <container_id>

- ####  Stop the container. A SIGKILL message will be fired to kill immediately your container, this way you cannot do anything before the container ends
        $> docker kill <container_id>

- ####  Execute a command on the specified container, -it allows us to provide input to the container, in other words, -it = iteratively
    **-i** attach to the STDIN linux process, default receive input process
    
    **-t** attach to the outputs processes STDOUT and STDERR in a nice look terminal
    
        $> docker exec -it <container_id> <command> 

- ####  Builds a new image based on the Dockerfile in the current directory
        $> docker build .

- ####  Tag the image, the comum pattern for that is -t docker_id/project_name:version, for example docker build -t erick/myproject:2.2.1 .
        $> docker build -t <image_tag> .

- ####  Create a image from a running container, -c set the default command to be executed when the container starts
        $> docker commit -c 'CMD ["redis-server"]' <container_id>

- ####  Attach the STDIN, STDOUT and STDERR to the primary process ("Example: npm") of the specified running container
        $> docker attach <container_id>

## Notes
* alpine is a term that means the smallest image as possible 
  * ex.: node:alpine
