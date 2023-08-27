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
# 









