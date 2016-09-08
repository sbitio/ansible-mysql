# *This role is abandoned.*

Mysql
=====

Configure Mysql service, optionally with a master-slave replication setup.

Tested in Debian Wheezy and CentOS 6.5. This role is not intrusive: distro's
config files are respected, with minimal adjustments. In RedHat
systems, Debian style `/etc/mysql/conf.d` is enabled to ease configuration.

This role is Work In Progress. See [`TODO` file](TODO) for some details.

Also, if [sbitmedia.monit](https://galaxy.ansible.com/list#/roles/729) is
present, a monit check is configured.

Role Variables
--------------

All accepted variables are documented in [`defaults/main.yml`](defaults/main.yml)
and [`vars/main.yml`](vars/main.yml).

Example Usage
-------------

Given two hosts (`db1` and `db2`) in group `dbservers`, here's an example setup
for master-slave replication:

`group_vars/dbservers`:
```yaml
mysql_root_pass: <secret>
mysql_repl_user:
  name: repl
  pass: <secret>
```

`host_vars/db1`:
```yaml
mysql_server_id: 1
mysql_repl_role: master
```

`host_vars/db2`:
```yaml
mysql_server_id: 2
mysql_repl_role: slave
mysql_repl_master: <ip of db1>
```

`site.yml`:
```yaml
- hosts: dbservers
  roles:
    - sbitmedia.mysql
```

To create users and databases see [Ansible's mysql modules](http://docs.ansible.com/list_of_database_modules.html).

License
-------

BSD

Author Information
------------------

Jonathan Araña Cruz - SB IT Media, S.L.

Credits
-------

Some ideas picked from [bennojoy.mysql](https://galaxy.ansible.com/list#/roles/1) role.

