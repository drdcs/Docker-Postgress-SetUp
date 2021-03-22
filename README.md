# Docker-Postgress-SetUp
process to setup postgres using docker via network

Postgres-DB(Docker) <--------- NETWORK(db) <------------ PSQL(Docker)
    |
    |
(Volume save data to local machine)

## Create a Network and name it as DB ?

```shell
docker network create db
docker network rm db  (to delete a network)
```

## How to mount the data as Volume ?

> Create a folder and navigate to the folder
  ```shell
  docker run --name db -p 5432:5432 --network=db \
  -v "$PWD:/var/lib/postgresql/data" -e POSTGRES_PASSWORD=password \
  -d postgres:alpine
  ```
  --name : name of the container
  --network: to which network we attach the postgres container to
  -v : Volumne to retain the Database 
  -e : environmental variable , here we have added the postgres_password
  -d : detach mode and the version (tag) of the postgres
