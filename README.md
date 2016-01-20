# Some simple things in Docker

## Getting Started
Clone the repo:
```bash
git clone git@github.com:drGrove/intro2docker
```

Bulid the local nginx image:
```bash
docker-compose build
```

Run the cluster:
```bash
docker-compose up -d
```

Get the port of the running nginx instance:
```bash
docker-compose ps -a
```

**NOTE for Mac Users**: You will need to check the IP of your running docker machine to access the API. By default, i've known the IP 
to be 192.168.99.100. This may be different than yours though.

Access the Clustered API:

1. Open Up a browser
2. Go to http://${HOST_IP}:${MOUNTED_PORT}
3. Refresh the screen and see the hostname change.
