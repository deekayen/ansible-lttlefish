# lttle-ansible-bootstrap

[![Build Status](https://travis-ci.org/deekayen/lttle-ansible-bootstrap.svg?branch=master)](https://travis-ci.org/deekayen/lttle-ansible-bootstrap) ![Unlicense](https://img.shields.io/badge/license-Unlicense-blue.svg)

I don't really intend for this repo to be consumed as a generic, re-usable
configuration. It's strictly intended to meet my personal needs.

Installs and configures various things with:

* Apache
* PHP
* ownCloud
* OpenVPN
* Dovecot/Postfix/procmail
* ntpd

If I'm really in an Ansible mood, I could generate a temporary
Linode API key and use Ansible to create my Atlanta-based Linode
using the standalone playbook in the directory root.

To keep the playbook idempotent and secure, the first time it runs, it
will create random passwords for the MariaDB root user, ownCloud, and
mail user. The passwords to those accounts will be saved on the remote
server in appropriate configuration files instead of in the global_vars
of this Ansible playbook like most other templates you'll find on
Github. Though these files are uploaded in-whole on the first run as
templates, they won't upload again after that because the remote server
is treated as the master copy of the passwords on these files:

* `/root/.my.cnf`
* `/var/www/owncloud/config/config.php`
* `/etc/dovecot/dovecot-sql.conf.ext`
* `/etc/postfix/mysql-virtual-alias-maps.cf`
* `/etc/postfix/mysql-virtual-mailbox-domains.cf`
* `/etc/postfix/mysql-virtual-mailbox-maps.cf`
