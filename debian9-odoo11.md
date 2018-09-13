# Odoo 11 en debian 9
Odoo 11.0-20180912 (Community Edition)

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
Para estar seguros, actualizamos
```
apt-get upgrade
```

Instalamos un modulo de python necesario
```
sudo pip3 install num2words
```

Ahora entramos en nuestra instalacion de ODOO

http://192.168.122.146:8069

Llenamos el formulario con los datos nuestros, y listo 

### phppgadmin

http://192.168.122.146/phppgadmin/
