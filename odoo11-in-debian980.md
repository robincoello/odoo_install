# Odoo 11 in Debian 9.8.0

We need install debian first


## Download Debian here: 

```
https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-9.8.0-amd64-netinst.iso
```
OR DVD 
```
https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/
```

user: pass

root :  linux

user : user


Now, install sudo module

```
su -

apt-get install sudo -y 
```

Now add user a sudo group

```
usermod -aG sudo user
```


Install SSH if you need conecte from other machine

```
 apt-get install ssh  
```


## ODOO

https://www.odoo.com/documentation/11.0/setup/install.html

We want the version 11 and Packaged installers

These packages automatically set up all dependencies (for the Community version), but may be difficult to keep up-to-date.

### Prepare

Odoo needs a PostgreSQL server to run properly. The default configuration for the Odoo ‘deb’ package is to use the PostgreSQL server on the same host as your Odoo instance. Execute the following command as root in order to install PostgreSQL server :

```
 apt-get install postgresql -y
```

```
 apt-get install phppgadmin pgadmin3 wkhtmltopdf -y

```

### Repository

Odoo S.A. provides a repository that can be used with Debian and Ubuntu distributions. It can be used to install Odoo Community Edition by executing the following commands as root:

```
  wget -O - https://nightly.odoo.com/odoo.key | apt-key add -
  
  echo "deb http://nightly.odoo.com/11.0/nightly/deb/ ./" >> /etc/apt/sources.list.d/odoo.list
  
  apt-get update && apt-get install odoo -y

```
You can go to ODOO web 

http://1270.0.1:8069

### phppgadmin

http://127.0.0.1/phppgadmin/


You can then use the usual apt-get upgrade command to keep your installation up-to-date.


Others modules 
```
sudo pip3 install num2words
```












