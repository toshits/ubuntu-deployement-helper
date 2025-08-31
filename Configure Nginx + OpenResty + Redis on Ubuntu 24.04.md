#### Update packages of Ubuntu
```bash
apt update
```

```bash
apt upgrade
```

#### Install OpenResty

```bash
# Add OpenResty repository
sudo apt install -y wget gnupg ca-certificates lsb-release

wget -O - https://openresty.org/package/pubkey.gpg | sudo gpg --dearmor -o /usr/share/keyrings/openresty.gpg
echo "deb [signed-by=/usr/share/keyrings/openresty.gpg] http://openresty.org/package/ubuntu $(lsb_release -sc) main" | \
  sudo tee /etc/apt/sources.list.d/openresty.list

# Install OpenResty + Redis client lib
sudo apt update
sudo apt install -y openresty luarocks redis-server

# Install lua-resty-redis library
sudo luarocks install lua-resty-redis
```

#### Start Redis Server
```bash
systemctl enable redis-server
```

#### Create nginx openresty proxy config

```bash
sudo nano /usr/local/openresty/nginx/conf/nginx.conf
```

```nginx
# Sample config uses redis get the host and port mapping
worker_processes auto;
events {
    worker_connections 1024;
}

http {
    lua_shared_dict cache 10m;

    upstream theme_3001 {
        server 127.0.0.1:3001;
    }
    upstream theme_3002 {
        server 127.0.0.1:3002;
    }
    upstream theme_3003 {
        server 127.0.0.1:3003;
    }

    server {
        listen 80;
        server_name _;

        location / {
            set $backend "";

            access_by_lua_block {
                local redis = require "resty.redis"
                local red = redis:new()
                red:set_timeout(100)

                local ok, err = red:connect("127.0.0.1", 6379)
                if not ok then
                    ngx.log(ngx.ERR, "failed to connect to redis: ", err)
                    return ngx.exit(502)
                end

                local domain = ngx.var.host
                local port, err = red:get(domain)

                if not port or port == ngx.null then
                    ngx.log(ngx.ERR, "no mapping found for ", domain)
                    return ngx.exit(404)
                end

                ngx.var.backend = "http://127.0.0.1:" .. port
            }

            proxy_pass $backend;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
    }
}
```

#### Test nginx for syntax and errors
```bash
sudo /usr/local/openresty/nginx/sbin/nginx -t
```

#### Restart he openresty nginx server
```bash
sudo systemctl restart openresty
```

> **_NOTE:_** Do not forger to start your web server at 3000 and map the domain and port in the redis