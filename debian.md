# Install in Debian

```
su -
```

Now 

```

wget -O - https://nightly.odoo.com/odoo.key | apt-key add -
echo "deb http://nightly.odoo.com/9.0/nightly/deb/ ./" >> /etc/apt/sources.list
apt-get update && apt-get install odoo

apt-get install postgresql postgresql-server  postgresql-client -y
apt-get install phppgadmin pgadmin3 wkhtmltopdf -y

exit

sudo service odoo start

```

now open in your broswer 

http://0.0.0.0:8069


