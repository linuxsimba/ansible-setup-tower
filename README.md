ansible-tower-setup
=========

A role to configure multi node Tower installation with an option to configure
database nodes

This role installs the Ansible Tower setup playbook and appends Sam Doran's
postgres replication role for configuring streaming replication if needed.

Requirements
------------

* Ansible 2.3+
* RHEL/Centos Nodes.
* Ubuntu Latest LTS

Role Variables
--------------

* ``ansible_tower_version``: Defaults to ``latest``. Change it to a tower version if
  needed for example ``3.1.3``.

* ``tower_install_url``: Defaults to install the latest Tower install playbook (_no
  bundle_). Change this variable if you wish to download a Setup bundle. For
example: ``http://releases.ansible.com/ansible-tower/setup-bundle/ansible-tower-setup-bundle-latest.el7.tar.gz ``

* ``postgres_streaming_replication``: Defaults to ``true``. If set to true assumes
  you want to this role to create a pair of postgres database servers with
  streaming replication enabled

* ``tower_servers``: List of DNS names of Ansible Tower servers

* ``postgres_server``: List of DNS names of Postgres servers. List only **2**
  servers. The first server is the master server. The 2nd server is a slave server.


Dependencies
------------

None

Example Playbook
----------------

```
  - hosts: tower_install
    roles:
      - role: setup-tower
        ansible_tower_version: 3.1.3
```

License
-------

MIT

Author Information
------------------

Stanley Karunditu (stanley at linuxsimba dot com )
