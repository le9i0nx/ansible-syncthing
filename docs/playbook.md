

```YAML
---

- name: Prepare core environment
  hosts: [ 'debops_all_hosts', 'debops_service_syncthing', 'test_hosts' ]
  become: False

  roles:

    - role: debops.core
      tags: [ 'role::core' ]
      become: True

- name: syncthing install
  hosts: [ 'debops_all_hosts', 'debops_service_syncthing', 'test_hosts' ]
  become: True
  become_method: sudo

  roles:

    - role: le9i0nx.syncthing
      tags: [ 'role::syncthing' ]

```
