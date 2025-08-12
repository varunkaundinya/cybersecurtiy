# 🐧 Linux Commands Reference

A comprehensive list of essential Linux commands, categorized for easy learning and reference.

---

## 📂 File & Directory Management

| Command | Description | Example |
|---------|-------------|---------|
| `pwd` | Show current working directory | `pwd` |
| `ls` | List files and directories | `ls -l` (detailed list) |
| `cd` | Change directory | `cd /home/user` |
| `mkdir` | Create directory | `mkdir myfolder` |
| `rmdir` | Remove empty directory | `rmdir myfolder` |
| `rm` | Remove files/directories | `rm file.txt`, `rm -r folder` |
| `touch` | Create empty file | `touch file.txt` |
| `cp` | Copy files/directories | `cp file.txt backup/` |
| `mv` | Move or rename files/directories | `mv file.txt docs/` |
| `find` | Search files/directories | `find / -name file.txt` |
| `locate` | Quickly find files (requires `updatedb`) | `locate file.txt` |
| `tree` | Show directory tree | `tree /var` |

---

## 📄 File Viewing & Editing

| Command | Description | Example |
|---------|-------------|---------|
| `cat` | Display file content | `cat file.txt` |
| `less` | View file (page by page) | `less file.txt` |
| `more` | View file (older version of `less`) | `more file.txt` |
| `head` | Show first 10 lines | `head file.txt` |
| `tail` | Show last 10 lines | `tail file.txt` |
| `nano` | Edit file with Nano editor | `nano file.txt` |
| `vim` | Edit file with Vim editor | `vim file.txt` |
| `gedit` | GUI text editor | `gedit file.txt` |

---

## 🔐 Permissions & Ownership

| Command | Description | Example |
|---------|-------------|---------|
| `chmod` | Change file permissions | `chmod 755 script.sh` |
| `chown` | Change file owner | `chown user file.txt` |
| `chgrp` | Change group ownership | `chgrp developers file.txt` |
| `umask` | Set default permissions | `umask 022` |

---

## 📊 File Compression & Archiving

| Command | Description | Example |
|---------|-------------|---------|
| `tar` | Create/Extract archives | `tar -cvf backup.tar folder/` |
| `gzip` | Compress file | `gzip file.txt` |
| `gunzip` | Decompress `.gz` file | `gunzip file.txt.gz` |
| `zip` | Create zip file | `zip archive.zip file.txt` |
| `unzip` | Extract zip file | `unzip archive.zip` |

---

## 🌐 Networking Commands

| Command | Description | Example |
|---------|-------------|---------|
| `ping` | Test network connectivity | `ping google.com` |
| `ifconfig` | Show network interfaces (old tool) | `ifconfig` |
| `ip` | Show IP configuration | `ip addr show` |
| `netstat` | Show network connections | `netstat -tulnp` |
| `ss` | Show socket statistics | `ss -tuln` |
| `curl` | Fetch data from URL | `curl https://example.com` |
| `wget` | Download files | `wget https://file.com/file.zip` |
| `scp` | Securely copy files between systems | `scp file.txt user@host:/path` |
| `sftp` | Secure file transfer | `sftp user@host` |
| `ssh` | Secure shell login to remote system | `ssh user@host` |

---

## ⚙️ Process Management

| Command | Description | Example |
|---------|-------------|---------|
| `ps` | Show running processes | `ps aux` |
| `top` | Real-time process viewer | `top` |
| `htop` | Interactive process viewer | `htop` |
| `kill` | Terminate process by PID | `kill 1234` |
| `killall` | Kill processes by name | `killall firefox` |
| `jobs` | Show background jobs | `jobs` |
| `fg` | Bring background job to foreground | `fg %1` |
| `bg` | Resume background job | `bg %1` |

---

## 💾 Disk Usage & Management

| Command | Description | Example |
|---------|-------------|---------|
| `df` | Show disk usage | `df -h` |
| `du` | Show folder size | `du -sh folder/` |
| `lsblk` | List block devices | `lsblk` |
| `mount` | Mount filesystem | `mount /dev/sda1 /mnt` |
| `umount` | Unmount filesystem | `umount /mnt` |
| `blkid` | Show block device UUIDs | `blkid` |
| `parted` | Partition disk | `sudo parted /dev/sda` |

---

## 🛡️ User Management

| Command | Description | Example |
|---------|-------------|---------|
| `whoami` | Show current username | `whoami` |
| `who` | Show logged-in users | `who` |
| `id` | Show user ID and groups | `id user` |
| `adduser` | Add a new user | `sudo adduser newuser` |
| `usermod` | Modify user details | `usermod -aG sudo user` |
| `passwd` | Change password | `passwd user` |
| `deluser` | Remove a user | `sudo deluser user` |

---

## 🔍 Search & Filters

| Command | Description | Example |
|---------|-------------|---------|
| `grep` | Search text in files | `grep "error" logfile.txt` |
| `egrep` | Extended grep | `egrep "error|warning" logfile.txt` |
| `fgrep` | Fixed string grep | `fgrep "exact text" file.txt` |
| `awk` | Text processing | `awk '{print $1}' file.txt` |
| `sed` | Stream editor (find/replace) | `sed 's/old/new/g' file.txt` |

---

## ⏱️ Scheduling & Automation

| Command | Description | Example |
|---------|-------------|---------|
| `cron` | Schedule tasks | `crontab -e` |
| `at` | Schedule one-time task | `echo "ls" | at now + 2 minutes` |
| `systemctl` | Manage services | `systemctl restart apache2` |

---

## 🖥️ System Information

| Command | Description | Example |
|---------|-------------|---------|
| `uname` | Show system info | `uname -a` |
| `hostname` | Show system hostname | `hostname` |
| `uptime` | Show uptime | `uptime` |
| `date` | Show date and time | `date` |
| `cal` | Show calendar | `cal` |
| `lscpu` | Show CPU details | `lscpu` |
| `free` | Show memory usage | `free -h` |

---

## 🧹 System Cleanup

| Command | Description | Example |
|---------|-------------|---------|
| `clear` | Clear terminal | `clear` |
| `history` | Show command history | `history` |
| `alias` | Create command shortcut | `alias ll='ls -l'` |
| `unalias` | Remove alias | `unalias ll` |

---

✅ **Tip:** You can get more info about any command using:
```bash
man command_name
