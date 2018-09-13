# Odoo 11 en debia 9

En una maquina recien instalada

Instalar net-tools
```
sudo apt-get install net-tools
```

Conectarse al servidor 
```
ssh user@192.168.122.146
```

Seguiremos las instrucciones base de 

https://www.odoo.com/documentation/11.0/setup/install.html

Preparamos:
```
sudo apt-get install postgresql -y

sudo apt-get install phppgadmin pgadmin3 wkhtmltopdf -y

```

Ahora para ODOO
```
su

wget -O - https://nightly.odoo.com/odoo.key | apt-key add -
echo "deb http://nightly.odoo.com/11.0/nightly/deb/ ./" >> /etc/apt/sources.list.d/odoo.list
apt-get update && apt-get install odoo
```