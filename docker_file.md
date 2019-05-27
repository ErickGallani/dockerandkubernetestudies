- ## Dockerfile example
        # Specify a base image
        FROM node:alpine

        # Define a default work directory
        WORKDIR /my/app

        # Copy files to the intermidiate container in this case package.json
        COPY ./package.json ./

        # Install dependencies
        RUN npm install

        # Copy more files, this approach is good to prevent unnecessary re-build because if docker detects that the index.js have changed, than, all the following commands will be executed
        COPY ./index.js ./

        # Default command
        CMD [ "npm", "start" ]

- ## Build command example
        $> docker build -t repository/projectname:version .

- ## From, Run and Cmd commands
![Build pipeline](/assets/dockerfile_build_process.PNG "Build pipeline")

- ## From, Run and Cmd commands
![Overall build process](/assets/overall_view_build_process.PNG "Overall build process")

- ## From, Run and Cmd commands
![Build commands](/assets/docker_build_commands.PNG "Build commands")

- ## Copy Command
![Dockerfile copy command](/assets/docker_file_copy_command.PNG "Dockerfile copy command")

- ## Workdir Command
![Workdir command](/assets/workdir_command.PNG "Workdir command")


- ## Docker volume
![Docker volume](/assets/docker_volume.PNG "Docker volume")

- ## Docker volume run command
![Docker volume run command](/assets/docker_volume_command.PNG "Docker volume run command")


# Multistep build process
A Dockerfile can be split in multistep process to be able to use multiple base images

- Dockerfile multistep example

```
# Step 1 - Build step from the multistep Dockerfile
FROM node:alpine as builder

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

CMD ["npm", "run", "build"]

# Step 2 - Run the application built on the first step
FROM nginx

COPY --from=builder /app/build /usr/share/nginx/html
```