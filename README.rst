============================================================
Foreman Ansible Playbook supporting PostgreSQL and powerdns
============================================================

|Travis| |License|

.. |Travis| image:: https://img.shields.io/travis/adfinis-sygroup/foreman-ansible.svg?style=flat-square
   :target: https://travis-ci.org/adfinis-sygroup/foreman-ansible
.. |License| image:: https://img.shields.io/github/license/adfinis-sygroup/foreman-ansible.svg?style=flat-square
   :target: LICENSE


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
please check the installation part at https://github.com/adfinis-sygroup/foreman-ansible

Examples
========
The templates directory contains example `foreman-yml`_ YAML templates to
give you a head start to bootstrap Foreman.

In addition the variables overwritten in vars/example.yml are the minimum
amount of variables that need to be defined, e.g. the MySQL role does not
create any users or databases by default.

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
.. _foreman-yml: https://github.com/adfinis-sygroup/foreman-yml
