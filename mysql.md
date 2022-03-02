### Server administration

`````
# ---
#  first check your cloud or hosting dashboard if there is any block that needs to be released
# ---

# ---
# on host check connection - 3306 default port mysql
# ---

netstat -ntl | grep 3306

# ---
# on host enable remote connection on config mysql
# 0.0.0.0 for all remote connections or specify an address
# ---

sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf

bind-address=0.0.0.0

# ---
# check local firewall
# like debian or centos distros
# ---

sudo ufw status
sudo firewall-cmd --list-all


`````

### Mysql administration 

`````
# ---
# check user and permissions '%' --> remote
# ---

SELECT user, host FROM mysql.user;
SHOW GRANTS FOR ‘UserName’@‘%’;

# ---
# local user --> 'localhost'
# remote user --> '%' 
# ---

CREATE USER 'local_user'@'localhost' IDENTIFIED BY 'local_user_password';
CREATE USER 'remote_user'@'%' IDENTIFIED BY 'remote_user_password';

# ---
# all permissions
# ---

GRANT ALL PRIVILEGES ON prosa.* TO 'database_name'@'localhost';
GRANT ALL PRIVILEGES ON *.* TO 'remote_user'@'%' WITH GRANT OPTION;

# ---
# especific permissions
# reference: https://dev.mysql.com/doc/refman/5.6/en/grant.html#grant-quoting
# ---

GRANT SELECT, INSERT, UPDATE ON database_name.* TO 'local_user'@'localhost';


`````




