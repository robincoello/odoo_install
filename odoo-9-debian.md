# Odoo 9.0 en Debian 
Instalar odoo 9 para despues hacer una actualizacion a las versiones superiores y ver si es factible

## Version de linux
Linux debian 4.9.0-3-amd64 #1 SMP Debian 4.9.30-2+deb9u3 (2017-08-06) x86_64 GNU/Linux

## Manual usado
https://www.odoo.com/documentation/9.0/setup/install.html

## Paso a paso
* Agregamos al usuario normal con derechos de sudouser

```
usermod -aG sudo <username>
```

* Instalamos ssh 

```
sudo apt-get install ssh

```
Asi podemos conectarnos a distancia al servidor si asi o deseamos

Ahora la instalacion propia de odoo

```
# wget -O - https://nightly.odoo.com/odoo.key | apt-key add -
# echo "deb http://nightly.odoo.com/9.0/nightly/deb/ ./" >> /etc/apt/sources.list
# apt-get update && apt-get install odoo
```

Esto nos da el error sieguiente
```
Certains paquets ne peuvent être installés. Ceci peut signifier
que vous avez demandé l'impossible, ou bien, si vous utilisez
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.
L'information suivante devrait vous aider à résoudre la situation : 

Les paquets suivants contiennent des dépendances non satisfaites :
 odoo : Dépend: python-pypdf mais il n'est pas installable
        Recommande: antiword mais ne sera pas installé
        Recommande: postgresql mais ne sera pas installé
        Recommande: python-gevent mais ne sera pas installé
        Recommande: poppler-utils mais ne sera pas installé
E: Impossible de corriger les problèmes, des paquets défectueux sont en mode « garder en l'état ».

```
Ahora solucionamos asi: 
```
apt-get install antiword python-gevent poppler-utils
```





## Soluciones a problemas: 
https://github.com/odoo/odoo/issues/17002

buscar 

@dhiru1602 it is not that simple, Odoo code still depends on the old unmaintained python-pypdf

However, there is an easy workaround : create a fake python-pdf package and install python-pyPdf from Pipy (Python repository). All of this will be done as root :

    install equivs to create fake packages and python-pipto install package from Python repository
    run equivs-control python-pypdf, this will create and populate the file python-pypdf
    edit the file like below (dot and space under "Description" are mandatory) :

Section: python
Package: python-pypdf
Version: 1.13
Description: fake package to provide python-pypdf
 python-pypdf will need to be installed with pip
 .
 python-pypdf2  does not provide python-pypdf

    run equivs-build python-pypdf this will create the fake package python-pypdf_1.13_all.deb
    install the package with dpkg -i python-pypdf_1.13_all.deb
    run pip install pyPdf
    restart Odoo

See the complete tutorial on my blog :
http://zeroheure.info/how-to-install-odoo-on-latest-debian-ubuntu-without-python-pypdf-dependency/



