
#### Install MySQL
```bash
sudo apt install mysql-server
```

#### Open MySQL and Run

*~ MySQL initial configuration process*
```bash
sudo mysql
```

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'my-secret-password';
```

```bash
sudo mysql_secure_installation
```

#### Create New User & Grant Priviliges

```sql
CREATE USER 'root'@'%' IDENTIFIED BY 'PASSWORD';
```

```sql
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' WITH GRANT OPTION;
```

```sql
FLUSH PRIVILEGES;
```

Check users with host
```sql
SELECT User, Host FROM mysql.user;
```

#### Edit MySQL Config File

Edit: comment out - bind-address & mysqlx-bind-address
```shell
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```

Restart MySQL Service
```shell
sudo systemctl restart mysql
```

#### Open Port 3306 for HTTP Traffic

```shell
sudo ufw allow 3306
```




#deployment #mysql #ubuntu