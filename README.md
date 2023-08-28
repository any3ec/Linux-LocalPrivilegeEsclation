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
```
### For Founded Text Files(Sensitive Info):
replace your word with *:
```
grep -i *
```








