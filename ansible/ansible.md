##Ansible

* Simple   - Simple language 
* Powerful - Designed for multitier development 
* Agentless - Secure, reliable

##### Inventory File
```bash
hosts file
[logging]
1.1.1.1
2.2.2.2

[monitoring]
3.3.3.3
4.4.4.4
```

To run ping-pong module on above setup
```bash
ansible all --inventory-file=hosts --module-name ping  -vvvv -u opc --private-key=~/.ssh/id_rsa
```

#### Ansible Modules
Modules are Ansible’s way of abstracting certain system management or configuration tasks.
By abstracting commands and state into modules, Ansible is able to make system management idempotent.

    users
    groups
    packages
    ACLs
    files
    apache modules
    firewall rules
    ruby gems
    git repositories
    mysql and postgresql databases
    docker images
    AWS / Rackspace / Digital Ocean instances
    Campfire or Slack notifications

#### Playbook example
```yaml
- hosts: all
  pre_tasks:
    - name: Verify Ansible meets minimum version requirements
      assert:
        that: "ansible_version.full is version_compare('2.4.3', '>=')"
        msg: >
          "You must update Ansible to 2.4.3 or above to use this project."
      tags: always
  gather_facts: yes
  remote_user: opc
  become: yes
  roles:
    - common
  vars_files:
    - vars/common.yaml
```

* become - set to yes to activate privilege escalation.
* become_user - to set to required user
   `become_user: apache`

## Ansible galaxy
  Ansible Galaxy is Ansible’s official hub for sharing Ansible content. You can jump-start your automation project by using Galaxy with great content from the Ansible community
  * To create task
  
  `ansible-galaxy init cassandra.install`