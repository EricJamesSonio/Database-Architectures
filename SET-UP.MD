Find if using xampp! 
C:\xampp\mysql\bin\my.ini

Required! : Create the database first! 

1. Find something liek this...
[mysqld]
port=3306
socket=".../mysql/mysql.sock"
basedir="C:/xampp/mysql"
datadir="C:/xampp/mysql/data"

2. Add something liek this... (Replication settings!)
[mysqld]
server-id=1
log_bin=mysql-bin
bind-address=0.0.0.0
binlog_do_db=your_database_name

example:
[mysqld]
port=3306
basedir="C:/xampp/mysql"
datadir="C:/xampp/mysql/data"
server-id=1
log_bin=mysql-bin
bind-address=0.0.0.0
binlog_do_db=musicstore

3. Restart the mysql! 
Save and restart MySQL

Open your XAMPP Control Panel

Click Stop beside MySQL

Then click Start again

4. Verify if its working!
mysql -u root -p

5. Check the variables!
SHOW VARIABLES LIKE 'log_bin';
SHOW VARIABLES LIKE 'server_id';


< ------------------------------------------------------------------------------------------>
< ------------------------------------------------------------------------------------------>
< ------------------------------------------------------------------------------------------>
[This what i did]

< ------- MASTER DATABASE -------- (xampp/mysql)>
# The MySQL server
[mysqld]
port= 3306
socket = "/xampp/mysql/mysql.sock"
basedir = "/xampp/mysql"
tmpdir = "/xampp/tmp"
datadir = "/xampp/mysql/data"
pid_file = "mysql.pid"
# enable-named-pipe
key_buffer = 16M
max_allowed_packet = 1M
sort_buffer_size = 512K
net_buffer_length = 8K
read_buffer_size = 256K
read_rnd_buffer_size = 512K
myisam_sort_buffer_size = 8M
log_error = "mysql_error.log"

# Replication settings for MASTER
server-id=1
log_bin=mysql-bin
bind-address=0.0.0.0
binlog_do_db=musicstore

< ---------- SLAVE DATABASE ------- (xampp/mysql-slave)>
# The MySQL server (SLAVE)
[mysqld]
port=3307
socket="C:/xampp/mysql/mysql-slave.sock"
basedir="C:/xampp/mysql"
tmpdir="C:/xampp/tmp"
datadir="C:/xampp/mysql/data-slave"
pid_file="mysql-slave.pid"

# enable-named-pipe
key_buffer_size=16M
max_allowed_packet=1M
sort_buffer_size=512K
net_buffer_length=8K
read_buffer_size=256K
read_rnd_buffer_size=512K
myisam_sort_buffer_size=8M
log_error="C:/xampp/mysql/mysql-slave_error.log"

# Replication settings for SLAVE
server-id=2
relay-log=relay-bin
log_bin=mysql-bin
bind-address=0.0.0.0

# replicate only this database from master
replicate-do-db=musicstore




[Checking]
Windows 10@ERICJAMESSONIO c:\xampp
# mysql -u root -p
Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 10
Server version: 10.4.32-MariaDB-log mariadb.org binary distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]>


[Type after the MariaDB ]
MariaDB [(none)]> SHOW VARIABLES LIKE 'log_bin';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| log_bin       | ON    |
+---------------+-------+
1 row in set (0.001 sec)

MariaDB [(none)]> SHOW VARIABLES LIKE 'server_id';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| server_id     | 1     |
+---------------+-------+
1 row in set (0.000 sec)

MariaDB [(none)]>


