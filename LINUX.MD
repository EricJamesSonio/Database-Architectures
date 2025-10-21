< ---------------------------- LINUX UBUNTU TERMINAL COMMANDS -------------------------------->

Ctrl + Alt + T --> Open terminal

[BASICS]
| Command | Meaning                  | Example                    |
| ------- | ------------------------ | -------------------------- |
| `pwd`   | Show current directory   | → `/home/eric`             |
| `ls`    | List files and folders   | → `ls -l` (detailed view)  |
| `cd`    | Change directory         | `cd /etc/mysql/`           |
| `cd ..` | Go up one level          | From `/etc/mysql` → `/etc` |
| `cd ~`  | Go to home directory     |                            |
| `mkdir` | Make new folder          | `mkdir myproject`          |
| `rmdir` | Remove empty folder      | `rmdir testdir`            |
| `rm -r` | Remove folder & contents | `rm -r old_backup`         |

[Files Working]
| Command | Meaning                 | Example                     |
| ------- | ----------------------- | --------------------------- |
| `touch` | Create an empty file    | `touch notes.txt`           |
| `cat`   | View contents           | `cat notes.txt`             |
| `nano`  | Edit file (text editor) | `nano my.cnf`               |
| `cp`    | Copy file               | `cp file.txt /home/backup/` |
| `mv`    | Move or rename file     | `mv file.txt newname.txt`   |
| `rm`    | Delete file             | `rm old.txt`                |

[Utils]
Ctrl + O   # save
Enter      # confirm
Ctrl + X   # exit

[SUDO] - do as a superuser! (basically to be as admin! since some requires as admin!)
- Will grant perminssion , avoind denied!
sudo apt update
sudo apt install mysql-server
sudo systemctl restart mysql

[Package management]
| Command                         | Purpose                          |
| ------------------------------- | -------------------------------- |
| `sudo apt update`               | Update package info from servers |
| `sudo apt upgrade`              | Upgrade installed packages       |
| `sudo apt install mysql-server` | Install software                 |
| `sudo apt remove mysql-server`  | Uninstall software               |
| `sudo apt autoremove`           | Clean up unused dependencies     |
[example]
sudo apt update
sudo apt install mysql-server


[MySQL SUDO COMMANDS]
| Command                        | Meaning                           |
| ------------------------------ | --------------------------------- |
| `sudo systemctl status mysql`  | Check if MySQL is running         |
| `sudo systemctl start mysql`   | Start MySQL                       |
| `sudo systemctl stop mysql`    | Stop MySQL                        |
| `sudo systemctl restart mysql` | Restart MySQL                     |
| `sudo systemctl enable mysql`  | Start MySQL automatically on boot |

[Vieweing logs]
| File                       | Purpose            |
| -------------------------- | ------------------ |
| `/var/log/syslog`          | General system log |
| `/var/log/mysql/error.log` | MySQL errors       |
[examples]
Use cat, less, or tail to view them:

sudo tail -f /var/log/mysql/error.log

(-f = follow live updates)

[permissions]
Each file/folder has permissions:

r = read

w = write

x = execute
| Command | Description        |
| ------- | ------------------ |
| `ls -l` | View permissions   |
| `chmod` | Change permissions |
| `chown` | Change owner       |

[Network Basis]
| Command               | Purpose                 |
| --------------------- | ----------------------- |
| `hostname -I`         | Show your IP address    |
| `ping <ip>`           | Test network connection |
| `ufw status`          | Check firewall          |
| `sudo ufw allow 3306` | Allow MySQL port (3306) |

[Transferring Files Between Servers]

If you have two servers (Master & Replica), use scp:

scp /path/to/file.sql user@192.168.1.20:/tmp/


or, if on same machine:

cp db_dump.sql /tmp/

[Shortcuts]
| Shortcut   | What It Does               |
| ---------- | -------------------------- |
| `Ctrl + C` | Stop current command       |
| `Ctrl + L` | Clear terminal screen      |
| `history`  | Show command history       |
| `!!`       | Run the last command again |
| `Tab`      | Autocomplete               |
| `Up Arrow` | Show previous command      |

🧩 [PRACTICE LIST]

Here’s a small practice plan before setting up replication:

✅ Navigate directories (cd, ls, pwd)
✅ Edit files (nano, cat)
✅ Install MySQL (sudo apt install mysql-server)
✅ Restart MySQL (sudo systemctl restart mysql)
✅ Open MySQL shell (sudo mysql)
✅ Create a database, user, and table
✅ Copy a file using scp
✅ Check logs (tail -f /var/log/mysql/error.log)


