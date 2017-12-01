# install_ansible_tower
This role handles the installation of Ansible Tower Server and tower-cli.

## Requirements
- Preconfigured RHEL 7.x machine

## Usage

Basic usage to install Ansible Tower to a single host
```---
# Install basic tower to run on the required servers
- hosts: towers
  name: Install a basic tower instance ready for configuration
  roles:
    - install_ansible_tower
```