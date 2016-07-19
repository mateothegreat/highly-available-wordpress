# Setting up the Database

![](https://goo.gl/fYGZF7)

### Configuring the SQL Server
We need to create the wordpress database and add user access to it. This must be done by the shell or other SQL admin tool as Google does not support this with Second Generation SQL Instances.

```
root@gke-cluster-1-default-pool-a7bccc7b-47jj:/home/lenixx# mysql -h 104.198.35.169 -u root -pchangeme

mysql> CREATE DATABASE wordpress;
Query OK, 1 row affected (0.01 sec)

mysql> GRANT ALL PRIVILEGES ON wordpress.* TO 'changeme'@'%' IDENTIFIED BY 'changeme';
Query OK, 0 rows affected, 1 warning (0.00 sec)
```