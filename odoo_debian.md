# Odoo en Debian 

## Version de linux
Linux debian 4.9.0-3-amd64 #1 SMP Debian 4.9.30-2+deb9u3 (2017-08-06) x86_64 GNU/Linux

## Manual usado
https://www.odoo.com/documentation/11.0/setup/install.html

## Paso a paso





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



