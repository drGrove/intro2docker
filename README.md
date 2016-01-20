# Some simple things in Docker

## Getting Started
Clone the repo:
```bash
git clone git@github.com:drGrove/intro2docker
```
Pick a subproject:
```bash
cd simple_cluster
```

Bulid the local  image(s):
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

### Proxying to the ouside world
**NOTE: This example is for Mac OSX. Please make the necessary changes for your distro**

Install Nginx:

```bash
brew install nginx
```

Edit Your nginx.conf
```bash
vim /usr/local/etc/nginx/nginx.conf
```
You will need to get your current docker port. You can lock this in by editing the docker-compose.yml to do the port map. 
Otherwise you'll want to urn `docker-compose ps -a` and grab the port number for the binding
```
server {
  listen 9999 default_server;
  
  location / {
    proxy_pass http://192.168.99.100:${INSERT_PORT_NUMBER_HERE};
  }
}
```

Restart nginx and bind to 0.0.0.0
```bash
sudo nginx
```

Access your server via the proxy:
http://0.0.0.0:9999

If you'd like to show this to your friends within your network. Give them your IP address from the command
`ifconfig`
