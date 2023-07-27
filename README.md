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
        root_users:
          - user:
              name: "root-user1"
              ssh: "ssh_root-user1"
          - user:
              name: "root-user2"
              ssh: "ssh_root-user2"
        standard_users:
          - user:
              name: "standard-user1"
              ssh: "ssh_standard-user1"
          - user:
              name: "standard-user2"
              ssh: "ssh_standard-user2"
      roles:
        - { role: ansible-role-ssh}

License
-------

Apache 2.0

Author Information
------------------

Cloud Labs shared roles
