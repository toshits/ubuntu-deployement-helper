#### Install Requires packages onto ubuntu vps
```bash
sudo apt install nginx certbot python3-certbot-nginx
```

#### Allow firewall to allow nignx
```shell
sudo ufw allow "Nginx Full"
```

#### Install Nodejs and PM2
```shell
sudo apt install nodejs
```

```shell
sudo npm install pm2 -g
```

#### Go to /var/www & Add the nextjs app folder here
```shell
cd /var/www
```

#### Start app server with pm2
*For Production Build*
```shell
sudo pm2 start npm --name "next" -- start
```
*For Development*
```shell
sudo pm2 start npm --name "next" -- run dev
```

#### Setting up nginx configuration

```shell
cd /etc/nginx/sites-available
```

Create a sites-available file and Add the following code
```shell
sudo nano rovioco
```

Copy config file from here:-
https://gist.github.com/oelbaga/5019647715e68815c602ff05cff2416e#file-ubuntu-nextjs-nginx-config-file

Change nginx.conf file so that we don't need to add sites-enabled

```shell
sudo nano /etc/nginx/nginx.conf
```
*Change sites-enabled to sites-available*

Delete 'default' in /etc/nginx/sites-available
```shell
sudo rm /etc/nginx/sites-available/default
```

#### Add SSL to the domain
```shell
sudo certbot --nginx -d rovioco.com
```


For Nodejs express api nginx sites-available config file
https://chenosis.io/tutorials/configure-nginx-as-a-reverse-proxy-for-your-express-api#:~:text=server%20%7B%0A%20%20%20%20listen%2080%3B%0A%20%20%20%20server_name%20%20yourdomain.com%3B%0A%0A%20%20%20%20access_log%20/var/log/nginx/reverse%2Daccess.log%3B%0A%20%20%20%20error_log%20/var/log/nginx/reverse%2Derror.log%3B%0A%0A%20%20%20%20location%20/%20%7B%0A%20%20%20%20%20%20%20%20proxy_pass%20http%3A//127.0.0.1%3A3000%3B%0A%20%20%20%20%7D%0A%7D




#deployment #nextjs #ubuntu