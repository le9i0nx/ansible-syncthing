

```YAML
---

# syncthing
syncthing__dependencies_ferm: True

device_moto:
  - id: "0000000-0000000-0000000-0000000-0000000-0000000-0000000-0000000"
    name: "tapik"

device_awz_old:
  - id: "0000000-0000000-0000000-0000000-0000000-0000000-0000000-0000001"
    name: "tapik"

role_syncthing_user: 'user'
role_syncthing_data:
#  devices_add:
#    - "{{ device_moto }}"
  folders:
    - inventory_hosts: '{{ groups.homes }}'
      path: '/home/user/crypt/'
      id: 'crypt'
    - inventory_hosts: '{{ groups.homes }}'
      path: '/home/user/moto_e-photos/'
      id: 'moto_e-photos'
      devices_add:
        - "{{ device_moto }}"
    # http://docs.ansible.com/ansible/playbooks_filters.html#list-filters
    - inventory_hosts: '{{ groups.homes | difference(groups.awz) }}'
      path: '/home/user/music/'
      id: 'music'
      devices_del:
        - "{{ device_awz_old }}"
      devices_add:
        - "{{ device_moto }}"
    - inventory_hosts: '{{ groups.homes }}'
      path: '/home/user/money/'
      id: 'money'
      devices_add:
        - "{{ device_moto }}"
```

