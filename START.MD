# ==========================================================
# MASTER CONFIGURATION
# File: C:\xampp\mysql\bin\my.ini
# ==========================================================
[mysqld]
port=3306
socket="/xampp/mysql/mysql.sock"
basedir="/xampp/mysql"
tmpdir="/xampp/tmp"
datadir="/xampp/mysql/data"
pid_file="mysql.pid"

# Basic settings
key_buffer_size=16M
max_allowed_packet=1M
sort_buffer_size=512K
net_buffer_length=8K
read_buffer_size=256K
read_rnd_buffer_size=512K
myisam_sort_buffer_size=8M
log_error="mysql_error.log"

# Replication settings (MASTER)
server-id=1
log_bin=mysql-bin
bind-address=0.0.0.0
binlog_do_db=musicstore

# ==========================================================
# SLAVE CONFIGURATION
# File: C:\xampp\mysql-slave\bin\my.ini
# ==========================================================
[mysqld]
port=3307
socket="C:/xampp/mysql-slave/mysql.sock"
basedir="C:/xampp/mysql-slave"
tmpdir="C:/xampp/mysql-slave/tmp"
datadir="C:/xampp/mysql-slave/data"
pid_file="mysql-slave.pid"
skip-slave-start
skip-networking=0

# Basic settings
key_buffer_size=16M
max_allowed_packet=1M
sort_buffer_size=512K
net_buffer_length=8K
read_buffer_size=256K
read_rnd_buffer_size=512K
myisam_sort_buffer_size=8M
log_error="C:/xampp/mysql-slave/mysql-slave_error.log"

# Replication settings (SLAVE)
server-id=2
relay-log=slave-relay-bin
relay-log-index=slave-relay-bin.index
log_bin=mysql-bin
bind-address=0.0.0.0

# Replicate only this database
replicate-do-db=musicstore

# InnoDB data locations
innodb_data_home_dir="C:/xampp/mysql-slave/data"
innodb_log_group_home_dir="C:/xampp/mysql-slave/data"

C:\
 └── xampp\
      ├── mysql\
      │    ├── bin\
      │    │    └── my.ini                 <-- Master config
      │    ├── data\                       <-- Master data folder
      │    │    ├── mysql\
      │    │    ├── performance_schema\
      │    │    └── musicstore\
      │
      ├── mysql-slave\
      │    ├── bin\                        <-- Copied from master’s bin
      │    │    ├── mysqld.exe
      │    │    ├── mysql.exe
      │    │    ├── my.ini                 <-- Slave config (edited)
      │    ├── data\                       <-- Empty (to be initialized)
      │    └── tmp\
      │
      └── tmp\                             <-- Optional shared temp folder



[INITILIZE SLAVE] - GIT BASH
/c/xampp/mysql-slave/bin/mysql_install_db.exe --datadir="C:/xampp/mysql-slave/data"


Expected output:
Running bootstrap
Removing default user
Creating my.ini file
Creation of the database was successful


[Start Both Master and Slave]
# Start master
/c/xampp/mysql/bin/mysqld.exe --defaults-file="C:\xampp\mysql\bin\my.ini"


# Start slave
/c/xampp/mysql-slave/bin/mysqld.exe --defaults-file="C:\xampp\mysql-slave\bin\my.ini"


# Kill Server (using CMD)
taskkill /F /IM mysqld.exe

[Verification Commands]

On MASTER (port 3306):
SHOW MASTER STATUS;


On SLAVE (port 3307):
SHOW SLAVE STATUS\G


