============================================================
Foreman Ansible Playbook supporting PostgreSQL and powerdns
============================================================

|Travis| |License|

.. |Travis| image:: https://img.shields.io/badge/license-GPLv3-blue.svg
   :target: LICENSE
.. |License| image:: https://img.shields.io/badge/author-Hamza-blue.svg
   :target: https://naper.eu
.. |License| image:: https://img.shields.io/badge/c-ABlogix-yellow.svg
   :target: https://ablogix.fr

.. image:: https://raw.githubusercontent.com/theforeman/foreman-graphics/master/logo/foreman_medium.png

.. image:: https://www.linuxtricks.fr/upload/ansible.png

Quick Informations ?
----------------------

* Only for PostgreSQL with support for powerdns
* For Mysql please check https://github.com/adfinis-sygroup/foreman-ansible
* This playbook is using the repo https://github.com/adfinis-sygroup/foreman-ansible

Features
========
The goal of this playbook is to offer a fully automated way to deploy a
complete and ready-to-use Foreman instance within minutes.

It contains multiple different roles with numerous customizable variables,
which provide the following features:

* setup database (PostgreSQL)
* setup webserver (plain nginx as a proxy or nginx-passenger)
* setup isc-dhcp-server
* setup TFTP server
* Setup powerdns
* setup foreman-proxy
* setup Foreman including configuration (templates, hosts, domains, etc.)

**None of the roles will install Puppet or use the official foreman-installer,
instead the plain Foreman packages are used!**

In addition this playbook makes use of `foreman-yml`_ to automatically configure
Foreman through the API based on a YAML file, which includes adding all
templates, OS, media, hosts, etc. and linking them accordingly.

Please note that at the current time the following distributions are supported:

* Debian 7 & 8
* Ubuntu 14.04 & 16.04
* CentOS 6 & 7
* Red Hat Enterprise Linux 6 & 7

Requirements
============
The target machine should fulfill the following requirements before the
playbook is applied:

* FQDN configured
* SELinux disabled
* Required ports 67, 69, 80, 443, etc. open
* Internet and repository access (e.g. Red Hat Optional repository)

**Ansible 2.0+ is required to use this playbook!**

Installation
============
Please check the installation part at https://github.com/adfinis-sygroup/foreman-ansible#installation

Roles
=====
Below a short overview of all included roles:

+-----------------+----------------------------------------------------+
| Name            | Description                                        |
+=================+====================================================+
| common          | update apt cache                                   |
+-----------------+----------------------------------------------------+
| foreman         | add repos and install Foreman                      |
+-----------------+----------------------------------------------------+
| foreman_proxy   | add repos, install and configure foreman-proxy     |
+-----------------+----------------------------------------------------+
| foreman_yml     | configure the Foreman instance with `foreman-yml`_ |
+-----------------+----------------------------------------------------+
| isc_dhcp_server | install and configure isc-dhcp-server              |
+-----------------+----------------------------------------------------+
| pgsql           | install PgSQL, create users and databases          |
+-----------------+----------------------------------------------------+
| powerdns        | install and congifure powerdns                     |
+-----------------+----------------------------------------------------+
| nginx           | add upstream repos if requested and setup nginx    |
+-----------------+----------------------------------------------------+
| passenger_nginx | add repos and setup passenger-nginx                |
+-----------------+----------------------------------------------------+
| sqlite          | install sqlite and create db directory             |
+-----------------+----------------------------------------------------+
| tftp            | install and setup TFTP including PXE boot files    |
+-----------------+----------------------------------------------------+


License
=======
GNU GENERAL PUBLIC LICENSE Version 3

See the `LICENSE`_ file.

.. _LICENSE: LICENSE
.. _foreman-yml: https://github.com/invicnaper/foreman-ansible-postgres/foreman-yml
