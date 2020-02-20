# Waggle Node Software

## Running a test environment

Scratch space for debugging RabbitMQ shovels and trying data stack spin up.

### Configuration

The node configuration can be found in `waggle-node.env`. A typical configuration specifies a node ID and a beehive hostname.

```text
WAGGLE_NODE_ID=0000000000000001
WAGGLE_BEEHIVE_HOST=host.docker.internal
```

### Commands

To start the node environment, run:

```sh
./node.up.sh
```

To stop the node environment, run:

```sh
./node.down.sh
```

To view logs from the node environment, run:

```sh
./node.logs.sh
```

### Adding Plugins

This is under major development! It will eventually be handled by our resource manager, but for now we have some manual tools to handle this.

First, we'll assume you've already started a node environment.

Now, we'll generate a configuration file with the single plugin `waggle/plugin-simple:0.1.0`.

```sh
python3 set-node-plugins.py waggle/plugin-simple:0.1.0
```

This will update the `docker-compose.plugins.yml` file and is ready for deployment. Simply start the environment again with

```sh
./node.up.sh
```

This will detect the configuration changes and update the environment.
