## 📢 Basic Commands:
---
Delete User ➙  `deluser user_name`  
Remove installation package ➙ `yum remove postgresql*`  
Package Check ➙ `yum list installed | grep post`  
Show all (including hidden) ➙ `ls -a`  
Lists files in sub-directories as well ➙ `ls -R`  
User Details of Password history ➙ `sudo chage -l username`  
Search specific package ➙ `sudo yum list --installed | grep nexus`  

## 📢 Problem and Solutions:
---
### 🎯 userdel: user sonar is currently used by process 3160

➣	First use `pkill or kill -9 <pid>` to kill the process.  
➣	Then use following userdel command t o delete user,  
`userdel -f cafe_fixer`

### 🎯 Fix HTTP Error 404 Not Found Trying Other Mirror CentOS 7

#### ➣	Run the following commands to search and replace the mirrors:

```
sudo sed -i s/mirror.centos.org/vault.centos.org/g /etc/yum.repos.d/*.repo
sudo sed -i s/^#.*baseurl=http/baseurl=http/g /etc/yum.repos.d/*.repo
sudo sed -i s/^mirrorlist=http/#mirrorlist=http/g /etc/yum.repos.d/*.repo
sudo -- bash -c 'echo "sslverify=false" >>/etc/yum.conf'
```     


### 🎯 How to remove this warning "This system is not registered to Red Hat Subscription Management. You can use subscription-manager to register."

```
vim /etc/yum/pluginconf.d/subscription-manager.conf  
enabled=0
```   

### 🎯 sudo sestatus command not found in ubuntu

➣   ```sudo apt-get install selinux-basics```   

### 🎯 root@192.168.140.139's password access denied in centos 9 when ssh login

1.	Check SSH Configuration:
	sudo vim /etc/ssh/sshd_config

	PasswordAuthentication yes
	PermitRootLogin yes

	sudo systemctl restart sshd

2.	Check SELinux:
	sudo sestatus
	SELinux configuration file is usually located at /etc/selinux/config.
SELINUX=disabled
3.	Firewall Settings:
	sudo firewall-cmd --list-all
	sudo firewall-cmd --permanent --add-service=ssh
	sudo firewall-cmd –reload

### 🎯 "internal/modules/cjs/loader.js:582 throw err"

 	node:internal/modules/cjs/loader:1031
 	  throw err;
 	  ^
 	
 	Error: Cannot find module 'express'
 	Require stack:
 	- /root/mongo-docker/js-app/app/server.js
 	    at Function.Module._resolveFilename (node:internal/modules/cjs/loader:1028:15)
 	    at Function.Module._load (node:internal/modules/cjs/loader:873:27)
 	    at Module.require (node:internal/modules/cjs/loader:1100:19)
 	    at require (node:internal/modules/cjs/helpers:119:18)
 	    at Object.<anonymous> (/root/mongo-docker/js-app/app/server.js:1:15)
 	    at Module._compile (node:internal/modules/cjs/loader:1198:14)
 	    at Object.Module._extensions..js (node:internal/modules/cjs/loader:1252:10)
	Solution: 
•	Delete the node_modules directory
•	Delete the package-lock.json file
•	Run npm install
•	Run npm start
