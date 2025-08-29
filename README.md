# Step-by-step guide to run a DTN Full Node

A full node consists of the following:

- **The DTN network**: A docker process to manage the node communications with the DTN network
- **AI processes**: Services that can process AI requests

## Step 1 - Update `full_config.yaml`

1. Update `node` section. Include your `username` and `nodeName`. If you don't have these need to create them on the node manager contract
2. Update `models`. List all the models served by adjacent AI processes.
3. Configure `sidecars`. Include your image name, relevant env variables, and docker images. You can configure multiple AI sidecars.

## Step 2 - `setup.sh`

Run `setup.sh` to create the `docker-compose` folder.

Go inside the docker-compose folder: `cd docker-compose`


## Step 3 - Configure private keys

You need two keys: Worker and the Staker. The Staker, is only required if you are configuring the node. For serving requests you only need the worker key.

**Add keys to keystore**

```
$  ./keystore.sh create $PRIVATE_KEY
```

*NOTE: MAKE SURE TO INCLUDE A SPACE BEFORE YOUR COMMAND (e.g. `<space>keystore.sh`). This will not include the command in your shell history. Otherwise you can leak the private key into the shell history

Above command will print a key such as `ccc....`

Copy this key in the `dtn-network.yaml`, `keys` section

## Step 4 - Run the node

If you have configured the node correctly you can simply run the node using docker-compose

```
$ docker-compose up -d


$ docker-compose logs
```


