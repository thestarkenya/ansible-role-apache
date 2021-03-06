# Ansible Role: Apache

[![Build Status](https://img.shields.io/travis/thestarkenya/ansible-role-apache.svg)](https://travis-ci.org/thestarkenya/ansible-role-apache) [![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/thestarkenya/ansible-role-apache/master/LICENSE)

Installs and configures Apache on RHEL/CentOS ~~or Debian/Ubuntu~~.

## Requirements

None

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
apache_listen_port: 80

apache_vhosts_use_template: true
apache_vhosts_file: vhosts.conf
apache_vhosts_hosts: []
```

## Dependencies

None

## Example Playbook

```yaml
- hosts: servers

  vars_files:
    - vars/main.yml

  roles:
    - role: ansible-role-apache
```

Inside `vars/main.yml`:

```yaml
apache_vhosts_hosts:
  - servername: www.local.dev
    serveralias: local.dev
    documentroot: /var/www/html
    extra_parameters: |
      RewriteCond %{HTTP_HOST} !^www\. [NC]
      RewriteRule ^(.*)$ http://www.%{HTTP_HOST}%{REQUEST_URI} [R=301,L]

# ... etc ...
```

## License

MIT
