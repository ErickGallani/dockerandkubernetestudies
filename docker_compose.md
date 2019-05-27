When you create a serie of services in a docker compose, all those services shares automatically the same network, therefore, they are able to communicate with each other.

## Dockerfile example using the Dockerfile to build a new image
```
    version: '3'
    services:
        redis-server:
            image: 'redis'
        node-app:
            build: .
            ports:
            - "5050:8095"
```

If you execute this docker compose file for the first time you're gonna to see something like this:

    Creating network "networkname_default" with the default driver

This means that right now, all your containers created by this compose can communicate with each other.

For if on that example you have a NodeJS app, you can connect to the redis container only by specify the service name, example:

## NodeJS App index.js example
```
    const express = require("express");
    const redis = require("redis");

    const app = express();
    const client = redis.createClient({
        host: 'redis-server' /* <--- service name created by docker compose specified on the docker-compose file */
    });
    client.set('visits', 0);

    app.get('/', (req, res) => {
        client.get('visits', (err, visits) => {
            res.send('Number of visits is ' + visits);
            client.set('visits', parseInt(visits) + 1);
        });
    });

    app.listen(8095, ()  => {
        console.log('Listening on port 8095');
    });
```

Notice that we have specified **host: 'redis-server'** instead of for example **host: 'https://localhost:9074'** or something like that. That's because docker compose create those alias for us.

Please note in this example we're using **build: .** because this compose runs in a project that have a docker build file **Dockerfile**

- #### Start a compose without specify a file. This will work if you create the file with the standard name (docker-compose.yml)
        $> docker-compose up

- #### Start a compose specifing a file.
        $> docker-compose -f my-compose.yml up

- #### Start a compose and build the Dockerfile
        $> docker-compose up --build

- #### Start a compose dettached from the process
        $> docker-compose up -d

- #### Stop all containers created by that compose
        $> docker-compose down

- #### Stop all containers created by that compose
        $> docker-compose down

- #### Docker compose to check the container status, need to be runned in the same directory within your docker-compose file or you need to specify the file path with -f
        $> docker-compose ps

- ## Docker compose up and down
![Docker compose up and down](/assets/docker-compose-up-down.PNG "Docker compose up and down")

- ## Docker compose restart policy
![Docker compose restart policy](/assets/docker_compose_restart_policy.PNG "Docker compose restart policy")
