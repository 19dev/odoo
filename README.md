## Docker Install

```sh
# Install docker
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
apt-cache policy docker-ce
sudo apt-get install -y docker-ce
sudo systemctl status docker

# Start a PostgreSQL server
docker run -d -e POSTGRES_USER=odoo -e POSTGRES_PASSWORD=odoo --name db postgres:9.4

# Start an Odoo instance
$ docker run -p 8069:8069 --name odoo --link db:db -t odoo
```

Web: http://localhost:8069

Oldukça iyi çalışıyor.

Kaynaklar
1. https://github.com/odoo/docker
2. https://hub.docker.com/_/odoo/
3. https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04

## Source Install
```sh
git clone https://github.com/odoo/odoo.git

sudo su - postgres -c "createuser -s $USER"

sudo apt-get install libsasl2-dev python-dev libldap2-dev libssl-dev
pip install -r requirements.txt

> In later debian (>jessie) and ubuntu (>14.04) you may need to add a symlink as npm packages call node but debian calls the binary nodejs
$ apt-get install -y npm
$ sudo ln -s /usr/bin/nodejs /usr/bin/node

$ sudo npm install -g less

$ ./odoo-bin
```

Test: http://localhost:8069/

Bad Request: Session expired (invalid CSRF token) hatası alıyoruz

```sh
2017-08-14 07:06:47,711 13718 WARNING xxx odoo.http: CSRF validation failed on path '/web/login'
2017-08-14 07:06:47,712 13718 INFO xxx werkzeug: 127.0.0.1 - - [14/Aug/2017 07:06:47] "POST /web/login HTTP/1.1" 400 -
```

Kaynaklar
1. https://www.odoo.com/documentation/10.0/setup/install.html

# Orginal

[![Build Status](http://runbot.odoo.com/runbot/badge/flat/1/10.0.svg)](http://runbot.odoo.com/runbot)
[![Tech Doc](http://img.shields.io/badge/10.0-docs-875A7B.svg?style=flat)](http://www.odoo.com/documentation/10.0)
[![Help](http://img.shields.io/badge/10.0-help-875A7B.svg?style=flat)](https://www.odoo.com/forum/help-1)
[![Nightly Builds](http://img.shields.io/badge/10.0-nightly-875A7B.svg?style=flat)](http://nightly.odoo.com/)

Odoo
----

Odoo is a suite of web based open source business apps.

The main Odoo Apps include an <a href="https://www.odoo.com/page/crm">Open Source CRM</a>,
<a href="https://www.odoo.com/page/website-builder">Website Builder</a>,
<a href="https://www.odoo.com/page/e-commerce">eCommerce</a>,
<a href="https://www.odoo.com/page/warehouse">Warehouse Management</a>,
<a href="https://www.odoo.com/page/project-management">Project Management</a>,
<a href="https://www.odoo.com/page/accounting">Billing &amp; Accounting</a>,
<a href="https://www.odoo.com/page/point-of-sale">Point of Sale</a>,
<a href="https://www.odoo.com/page/employees">Human Resources</a>,
<a href="https://www.odoo.com/page/lead-automation">Marketing</a>,
<a href="https://www.odoo.com/page/manufacturing">Manufacturing</a>,
<a href="https://www.odoo.com/page/purchase">Purchase Management</a>,
<a href="https://www.odoo.com/#apps">...</a>

Odoo Apps can be used as stand-alone applications, but they also integrate seamlessly so you get
a full-featured <a href="https://www.odoo.com">Open Source ERP</a> when you install several Apps.


Getting started with Odoo
-------------------------
For a standard installation please follow the <a href="https://www.odoo.com/documentation/10.0/setup/install.html">Setup instructions</a>
from the documentation.

If you are a developer you may type the following command at your terminal:

    wget -O- https://raw.githubusercontent.com/odoo/odoo/10.0/setup/setup_dev.py | python

Then follow <a href="https://www.odoo.com/documentation/10.0/tutorials.html">the developer tutorials</a>


For Odoo employees
------------------

To add the odoo-dev remote use this command:

    $ ./setup/setup_dev.py setup_git_dev

To fetch odoo merge pull requests refs use this command:

    $ ./setup/setup_dev.py setup_git_review

