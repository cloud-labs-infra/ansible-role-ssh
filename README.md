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
        add_users:
              - name: user1
                root_hosts: [172.17.0.2]
                std_hosts: [172.17.0.3]
                ssh: "ssh_user1"
              - name: user2
                root_hosts: [172.17.0.3]
                std_hosts: [172.17.0.2]
                ssh: "ssh_user2"
              - name: user3
                root_hosts: [172.17.0.3]
                std_hosts: []
                ssh: "ssh_user3"
        remove_users:
              - name: user3
                root_hosts: []
                std_hosts: [172.17.0.2, 172.17.0.3]
                ssh: "ssh_user3"
      roles:
        - { role: ansible-role-ssh}

License
-------

Apache 2.0

Author Information
------------------

Cloud Labs shared roles
