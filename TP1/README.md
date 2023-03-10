# __TP 1__

> ## __Database__

We chose to use a docker-compose from the get go to make it simpler

Passwords are kept in the `.env` file (gitignored)

But standards commands should look like this   
```docker
docker network create app-network
docker run --name pg_db -d -e POSTGRES_DB=db -e POSTGRES_USER=usr -e POSTGRES_PWD=pwd -v /storage:/var/lib/postgresql/data --net=app-network keelah/pg_db
docker run --name adminer -d -p 8080:8080 --net=app-network adminer
```

The docker compose have been commented for better readability

> ### Why should we run the container with a flag `-e` to give the environment variables?

So an user can easily change the password with the commandline and the password is not saved clearly in a file.  
This is why we chose to use a `.env` file to save our environment variables separate from our docker-compose. 

> ### Why do we need a volume to be attached to our postgres container?

So data can persist on the server even when we destroy the container. It acts as a local storage like a disk, storing the data.

> ## __Backend API__

The recommended openjdk image have been deprecated and recommends "to find and use suitable replacements ASAP".  
I have chosen to use the `eclipse-temurin` "Official Images for OpenJDK binaries built by Eclipse Temurin."

`docker run --name backend --net=app-network -p 8181:8080 --rm keelah/backend`


> ### __1-2__ Why do we need a multistage build? And explain each step of this dockerfile.

Multistage is used to keep ther size down by removing unused layers after building. We only need to use the RUN part of our image, not the source code used to build the app.


> ## __OUEB__

We got a simple synthwave themed web page going on
Nice :)


```
╭─ keelah     ~/Documents/CPE-Keelah    main ⇣1⇡1 *2 ?1 ▓▒░
╰─ docker stats
CONTAINER ID   NAME      CPU %     MEM USAGE / LIMIT     MEM %     NET I/O           BLOCK I/O    PIDS
3d3b404f62fe   adminer   0.00%     9.316MiB / 30.71GiB   0.03%     5.88kB / 0B       0B / 0B      1
bd550a8d6dd0   backend   0.08%     222MiB / 30.71GiB     0.71%     20.1kB / 13.9kB   0B / 131kB   49
e5cc8a1dc485   pg_db     0.01%     29.03MiB / 30.71GiB   0.09%     20kB / 14.3kB     0B / 496kB   17
e48b4a2c2a21   oueb      0.00%     4.992MiB / 30.71GiB   0.02%     9.45kB / 15.9kB   0B / 4.1kB   82
```
We got the default conf by executing this command
`docker cp oueb:/usr/local/apache2/conf/httpd.conf ./oueb/httpd.conf`


> ## __Docker Compose__

>### __1-3__ Document docker-compose most important commands
We use different commands with compose : 

- `docker-compose up`       Creates all the containers and starts them
- `docker-compose down`     Stops all the containers and removes them
- `docker-compose build`    Build all container images

>### __1-4__ Document your docker-compose file.
The docker-compose file is commented.

>### __1-5__ Document your publication commands and published images in dockerhub.
We published our 3 images on the Docker Hub via the username `Keelah` and they are named :
 * `keelah/oueb` httpd image
 * `keelah/pg_db` database image 
 * `keelah/backend` java web API

`docker login`  
THis allows us to log in to our own repo on docker hub

`docker tag keelah/backend:latest keelah/backend:1.0`  
With this command line we tag our built image with a tag version (here 1.0)

`docker push keelah/backend`  
With this command, the image is pushed to docker hub.