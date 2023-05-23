
### After First Time Login to VPS

#### Install Updates and Install Essential Build

```bash
sudo apt update
```

```bash
sudo apt upgrade
```

```bash
sudo apt install build-essential
```

#### Allow SSH access in the firewall configuration before activating the firewall

```shell
sudo ufw allow 'OpenSSH'
```

#### Allowing firewall

```shell
sudo ufw enable
```

#deployment #ubuntu 