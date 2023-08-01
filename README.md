Role Name
=========

Ansible role that manages user accounts and controls access to them with ssh keys

Role Variables
--------------

- root_users

    The root_users defines users with permission to run sudo without a password
    
    It is a list of dicts with fields:
    
    ```
    name: User's name.
    key: Path of ssh public key file.
    ```
- standard_users

    The standard_users defines users without permission to run sudo without a password
    
    It is a list of dicts with fields:
    
    ```
    name: User's name.
    key: Path of ssh public key file.
    ```

Example Playbook
----------------

    - name: Manage users
      hosts: hosts
      vars:
        users:
              - name: user1
                state: present
                sudo: yes
                ssh: ["ssh_user1"]
              - name: user2
                state: absent
                ssh: ["ssh_user2"]
      roles:
        - { role: ansible-role-ssh}

License
-------

Apache 2.0

Author Information
------------------

Cloud Labs shared roles
