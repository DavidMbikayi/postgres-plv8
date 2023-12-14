# PostGreSQL plv8 Docker Image

Repository builds docker image for postgresql 15 with the PVL8 Extensions. The DockerFile is a direct copy from:
    [PLV8 Official repo](https://github.com/plv8/plv8/tree/r3.2/platforms/Docker)
The image builds from the official postgresql image [Postgresql Docker info](https://hub.docker.com/_/postgres)

# How to use this image
## start a postgres instance
 `docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres`
The default postgres user and database are created in the entrypoint with initdb.

The postgres database is a default database meant for use by users, utilities and third party applications.

[Postgresdoc](postgresql.org/docs)

## ... or via psql
``` 
    $ docker run -it --rm --network some-network postgres psql -h some-postgres -U postgres
    psql (14.3)
    Type "help" for help.
    
    postgres=# SELECT 1;
    ?column?
    ----------
            1
    (1 row)
    ... via docker-compose or docker stack deploy
    Example docker-compose.yml for postgres:
```
  

## Use postgres/example user/password credentials

```
    version: '3.1'
    
    services:
    
        db:
            image: postgres
            restart: always
            environment:
            POSTGRES_PASSWORD: example
        
        adminer:
            image: adminer
            restart: always
            ports:
            - 8080:8080



