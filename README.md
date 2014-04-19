Mysql
=====

Configure Mysql service, optionally with a master-slave replication setup.

Leverages [sbitmedia.monit](https://galaxy.ansible.com/list#/roles/729) if present.

This role is Work In Progress. See [`TODO` file](TODO) for some details.

Some ideas picked from [bennojoy.mysql](https://galaxy.ansible.com/list#/roles/1) role.

Role Variables
--------------

All accepted variables are documented in [`defaults/main.yml`](defaults/main.yml)
and [`vars/main.yml`](vars/main.yml).

Example Playbook
----------------

```yaml
- hosts: dbservers
  roles:
    - mysql
```

License
-------

BSD

Author Information
------------------

Jonathan Araña Cruz - SB IT Media, S.L.

