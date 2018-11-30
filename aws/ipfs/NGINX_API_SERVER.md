# Start IPFS Gateway Server via Nginx

## Getting Started

### 1. Configuration IPFS (Optional)
This allow CORS for your IPFS API Server.

Config IPFS API Gateway with `cors-config.sh`
```bash
#!/bin/bash

ALLOW_ORIGINS='*'

# stop executing if anything fails
set -e

ipfs config --json API.HTTPHeaders.Access-Control-Allow-Origin '["*"]'
ipfs config --json API.HTTPHeaders.Access-Control-Allow-Methods '["PUT", "GET", "POST"]'
ipfs config --json API.HTTPHeaders.Access-Control-Allow-Credentials '["true"]'

echo "IPFS API CORS headers configured for $ALLOW_ORIGINS"
echo "Please restart your IPFS daemon"
```

Run `cors-config.sh`
```
sh cors-config.sh
```

Restart IPFS daemon

### 2. Install nginx
```shell
sudo apt update
sudo apt install nginx
```

### 3. Config nginx
```
sudo vi /etc/nginx/nginx.conf
```

Add these block to `nginx.conf` under `http` block 
```
...
    ##
    # Server
    ##

    server {
            listen          80;
            server_name     <HOSTNAME>;
            add_header      Access-Control-Allow-Origin *;

            location / {
                    proxy_pass          http://127.0.0.1:5001;
                    proxy_http_version  1.1;
                    proxy_set_header    Upgrade $http_upgrade;
                    proxy_set_header    Connection 'upgrade';
                    proxy_set_header    Host $http_host;
                    proxy_set_header    X-NginX-Proxy true;
            }
    }
...     
```

Start nginx server
```
sudo service nginx start
```

Try access your IPFS gateway
```
http://<HOSTNAME>/ipfs/<HASH>
```

## Resource 
https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04
http://single9.net/2018/03/nginx-reverse-proxy-server-and-socket-io/