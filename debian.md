# install odoo debian 
```
su -
```

Now 

```

wget -O - https://nightly.odoo.com/odoo.key | apt-key add -
echo "deb http://nightly.odoo.com/9.0/nightly/deb/ ./" >> /etc/apt/sources.list
apt-get update && apt-get install odoo

apt-get install postgresql postgresql-client -y
apt-get install phppgadmin pgadmin3 wkhtmltopdf -y

exit
```

now edit 
```
sudo nano /etc/odoo/odoo.conf
```
Like this

```
[options]
; This is the password that allows database operations:
; admin_passwd = admin
db_host = False
db_port = False
db_user = odoo
db_password = odoo
addons_path = /usr/lib/python2.7/dist-packages/odoo/addons
```
now

```
sudo service odoo start
sudo service postgresql start
sudo service apache2 start

```

now open in your broswer 
## Oddo
http://0.0.0.0:8069

## phppgadmin 
http://localhost/phppgadmin/


# Remove

sudo apt-get remove postgresql postgresql-client -y
sudo apt-get remove phppgadmin pgadmin3 wkhtmltopdf -y
sudo apt-get remove odoo -y
rm -r /etc/odoo/

rm -R /var/lib/postgresql/





