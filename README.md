Role Name
=========

ims: Ims

[![Build Status](https://travis-ci.org/cmihai-ansible/ims.svg?branch=master)](https://travis-ci.org/cmihai-ansible/ims)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.ims](https://galaxy.ansible.com/devops-toolbox.ims)

```bash
ansible-galaxy install devops-toolbox.ims
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
ims_packages_state: present
ims_remove_packages: true
ims_enable_service: true
ims_enable_selinux: true
ims_copy_templates: true
ims_firewall_configure: true
ims_firewall_rules:
  - service: ssh
  - port: 3389
ims_users:
  - user: devops
    group: docker
ims_selinux_booleans:
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
- name: Install ims on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: ims is configured
      import_role:
        name: devops-toolbox.ims
      vars:
        ims_packages_state: present
        ims_remove_packages: true
        ims_enable_service: true
        ims_enable_selinux: true
        ims_copy_templates: true
        ims_firewall_configure: true
        ims_firewall_rules:
          - service: ssh
          - port: 3389
        ims_users:
          - user: devops
            group: docker
        ims_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: ims
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
