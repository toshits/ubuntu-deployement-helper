
#### First, install the PPA to get access to its packages. From your home directory, use `curl` to retrieve the installation script for your preferred version

```bash
cd ~
curl -sL https://deb.nodesource.com/setup_16.x -o /tmp/nodesource_setup.sh
```

### Then run the script with `sudo`:
```bash
sudo bash /tmp/nodesource_setup.sh
```

### You can now install the Node.js package

```bash
sudo apt install nodejs
```

### Verify that you’ve installed the new version by running `node` with the `-v` version flag:

```shell
node -v
```

#deployment #nodejs