Role Name
=========

superset: Superset

[![Build Status](https://travis-ci.org/cmihai-ansible/superset.svg?branch=master)](https://travis-ci.org/cmihai-ansible/superset)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.superset](https://galaxy.ansible.com/devopstoolbox.superset)

```bash
ansible-galaxy install devopstoolbox.superset
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
superset_packages_state: present
superset_remove_packages: true
superset_enable_service: true
superset_enable_selinux: true
superset_copy_templates: true
superset_firewall_configure: true
superset_firewall_rules:
  - service: ssh
  - port: 3389
superset_users:
  - user: devops
    group: docker
superset_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install superset on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: superset is configured
      import_role:
        name: devopstoolbox.superset
      vars:
        superset_packages_state: present
        superset_remove_packages: true
        superset_enable_service: true
        superset_enable_selinux: true
        superset_copy_templates: true
        superset_firewall_configure: true
        superset_firewall_rules:
          - service: ssh
          - port: 3389
        superset_users:
          - user: devops
            group: docker
        superset_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: superset
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
