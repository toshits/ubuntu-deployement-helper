
### Install PM2

```shell
npm install pm2 -g
```

### Build the Production Version of Strapi

```shell
NODE_ENV=production npm run build
```

### Start Strapi server in production with PM2

Change the app to desired name

```shell
pm2 start npm --name app -- run start
```

### Save the PM2 so that after server restart app automatically starts

```shell
pm2 save
```

Note: Don't forget to allow strapi port in firewall