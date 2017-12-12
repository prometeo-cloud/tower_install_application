# tower_install_application

## Description:

This role installs Ansible Tower on a RHEL VM.

## Behaviour:

**Feature:** Install Ansible Tower

As a PaaS Operator
I want to install Ansible Tower

- **Scenario:** A RHEL VM is available
- **Given:** there is enough storage
- **Given:** there is enough memory
- **Given:** there is enough CPU
- **When:** the installation is executed
- **Then:** Ansible Tower is installed
- **Then:** Ansible Tower cli is installed

## Configuration:

A list of the external variables used by the role.

| Variable  | Description  | Example  | 
|---|---|---|
| **tower_dest**  | Location of Tower bundle download  | `/root` |
| **tower_version**  | Ansible Tower version  | 3.2.0-1.el7 |
| **tower_backup_dest**  | Location of Tower backup folder  | `/opt/backup` |

A preconfigured file containing the host IP address, **admin** username and password can be created on the vagrant box.  It should be in the following loaction:

`/root/.tower_cli.cfg`

The contents should be in the following format:

```
[general]
host = 192.168.10.50
username = admin
password = redhat123
```

## Testing:

The molecule test uses a vagrant box rather than a docker container, by default it will use a vagrant box called rhel74_sub.  This vagrant box will have already been configured for RHN subscription.

## Usage:

How to invoke the role from a playbook (this role must be run as `root`):

```---
# Install basic tower to run on the required servers
- hosts: towers
  become: true
  become_user: root
  name: Install Ansible Tower
  roles:
    - tower_install_application
```
