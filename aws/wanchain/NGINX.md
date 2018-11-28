# Start Wanchain JSON RPC Server via Nginx

## Getting Started

### 1. Install nginx
```shell
sudo apt update
sudo apt install nginx
```

### 2. Config nginx
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
                    proxy_pass          http://0.0.0.0:8545;
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

Try access your API endpoint
```
curl <HOSTNAME> -X POST -H "Content-Type: application/json" -d '{"jsonrpc":"2.0","method":"eth_syncing","params": [],"id":1}'
```

## Resource 
https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04
http://single9.net/2018/03/nginx-reverse-proxy-server-and-socket-io/