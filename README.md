[![Travis CI](http://img.shields.io/travis/le9i0nx/ansible-syncthing.svg?style=flat)](http://travis-ci.org/le9i0nx/ansible-syncthing) [![test-suite](http://img.shields.io/badge/test--suite-ansible--syncthing-blue.svg?style=flat)](https://github.com/le9i0nx/test-suite/tree/master/ansible-syncthing/) [![Ansible Galaxy](http://img.shields.io/badge/galaxy-le9i0nx.syncthing-660198.svg?style=flat)](https://galaxy.ansible.com/list#/roles/5258)



### Installation

This role requires at least Ansible `v2.0.0-0.7.rc2`. To install it, run:

    ansible-galaxy install le9i0nx.syncthing

### Documentation

playbook
```
---

- name: syncthing install pve
  hosts: pve
  become: True
  become_method: sudo

  roles:

    - role: le9i0nx.syncthing
      tags: [ 'role::syncthing', 'syncthing' ]
```

cat ./group_vars/pve.yml
```
---

role_syncthing:
  inventory_hosts: '{{ groups.pve }}'
  folders:
    path: '/var/lib/vz/template/iso/'
    id: 'vz_iso'

```

### Role dependencies

### Authors and license

`syncthing` role was written by:
- Aleksej Gavrilov | [e-mail](mailto:le9i0nx@gmail.com) | [GitHub](https://github.com/le9i0nx)

License: [MIT](https://github.com/le9i0nx/ansible-syncthing/blob/master/LICENSE)

