# Create a MongoDB replica database with 3 nodes

## Run the script
```
docker compose up
```

## Explanation
1. Two mongo containers are created, named `mongo-rs0-2` and `mongo-rs0-3`, with and the `--replSet` option, from the latest image of `mongo:latest`. They are also provided with volumes mapped to the folders `/data/rs0-2` and `/data/rs0-3` respectively.
2. The third container is created with the name `mongo-rs0-1` and `--replSet` option. This volume is mapped to the folder `/data/rs0-1`. This container is created from the modified version of the image `mongo:latest`. Here a `mongo.conf` file is provided to the container, which is used to configure the replica set.
3. Once all the containers are created, another short lived container called `setup-rs` is started. This container is created from the modified version of the image `mongo:latest`. Here a few files are provided:
    - `replicaSet.js` file is provided, which is used to configure the replica set.
    - `setup.sh` file is provided, which is used to run `replicaSet.js` on `mongo-rs0-1` container.
    - `wait-for-it.sh` file is provided, which is a utility function to wait for sometime and then run a script.

    The `setup-rs` container is then stopped.
4. `adminmongo` container is created. This is used to provide a web interface to the mongodb replica set.

## References
- [Creating a Mongo replicaset using docker: Mongo replicaset + Nodejs + Docker Compose](https://www.youtube.com/watch?v=mlw7vWISaF4)
