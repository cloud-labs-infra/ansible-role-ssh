ssh_user
=========

Ansible role that manages user accounts and controls access to them with ssh keys.

Requirements
------------

- SSH-server installed

Role Variables
--------------

All variables are defined as defaults in [defaults/main.yml](defaults/main.yml) and may be overrided.

| Name | Default value | Description |
|------|---------------|-------------|
| `users`| [] | A list of dicts with system users related information such as `name`, `state` (absent/present), extended sudo privileges required or not, a list of public ssh keys (key states are also supported - present (by default) or absent) |

Dependencies
------------

No

Example Playbook
----------------

```yaml
- hosts: all
  become: true
  roles:
    - { role: cloud_labs.ssh_user }
  vars:
    users:
    - name: user1
      state: present
      sudo: true
      ssh:
        - key: "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDX+D1/KugxvzTaUqKw0UowLK1hr0K2zejcQXChqvXzMDaq235Lerww4WKfn3F9GNNJFEwMkTWtEUuaXCd1k9Hxal19b+ItUxfnI6+SOhSGVDv+IDeTtzpdz1UkIiUy328nz2VXFW4E0PVkHbmozDKLE+GCENjhMKl5r4nfmncT/7QOKp7Mg30DZ8Ri/5ii4oePB47f1ODzBNlKpJIkBS8FIjIrhk/THHdgW+OGTSmwlp54Jn+bKPhE/7Gc0T9niFNHzQ4HVdK8CiLpNDzH7JyhNJKW/+IwOFIszyi0XpV+t4yEXCzxyBG/Xk2aHR4+dTz3l1oXyxP7biehWp2F8DbnrEiqImDy5pImRd7n1VT3CYTsDLgF0uwkaAF50ds+cNyFUJURixs8AXS1qCrEvNhaVUMcElaUWlItRwhxGJyk+pdhGYIUCBXh5le0/GQXVVNctqWNkelr4DhO9DcAeRNUO2Y/DvDPpZwc+XREZzxYlnWG7R/VK+5kjh1JOCPMJEM="
    - name: user2
      state: present
      sudo: true
      ssh:
        - key: "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC6cPaUleYMtowVtlOYPh7dfUa6msH1XYUEHpUCgCruWcAzr44LMqJXvBm0MIMO17qteYd641gqAgnpo7GEzZaXF3oALCnPz0aXq6AkV1ArfJDAA18zJ2lDDpVUthLita3rkl8Bnm2Z2x7iWjxqWTLR1yu0reRo2dkjKGJXwTIYn9mJY6vffSCPw7yOteb6n6Wvrow2C6QymFRwFRNW/JznKOasj7pFDNOQrc6AFLwIoBgYRr1sBNvxVDja6WVFbMnqpxvt5tfaKrwA7Vw2sTIzgMP+hAkJvDpeYgDiJWQhdtYfF13OZXgeEWYx5uIIM66polY9ZN9JTawkAzDoqi/Ybamtky9iL2TafOOK4B+9ZErvYs4j+AY35r2PQfR1WO9Q6N7bs8q9bk0CvV4wVBarnuT2lj2uQcoZTe/3xigVkKL4JdoINtkhIaPSdewTNKRao7G+oSJj+WLAR3qiyTh7Eym+gu2BQPrY+5+aXySUakDvm9AONni/e4cdPWt2MO8="
          state: absent
```

License
-------

Apache 2.0

Author Information
------------------

Cloud Labs shared roles
