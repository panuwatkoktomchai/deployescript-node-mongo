# Pre-requisite
- `Ansible` 2.6 or newer
- Target server should be able to use `apt`
    - Debian 7+
    - Ubuntu 16.04+
    - Any distributed fork from `ubuntu/debain`
- `python` 2.7+ on target server
- `docker` 18.05+ on target server
- `ssh` server 7.2+ on target server

# How to use
- Create your own inventory file in `inventory` directory
    - For examples

    ```
    ---
    server:
    hosts:
    <hostanme or ip>:
      ansible_user: <username>
      ansible_port: <ssh port>
    ```
- Run following command
    ```
    anible-playbook -i <inventory> <playbook>
    ```
    - You can deploy on specific services one of these database, API, CMS
        
        Example database
        ```
        ansible-playbook -i inventory/testserver api.yml -vvvv
        ```
    - Or you also can deploy whole services
        All services
        ```
        ansible-playbook -i inventory/testserver all.yml -e api_branch=master -e cms_branch=master
        ```
    Note: api branch will be `develop` by default if `-e api_branch=<branch>` or `-e front_end_branch=<branch>` is not defined


