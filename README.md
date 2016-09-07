# Ansible Role: Zabbix Repository

Installs the Zabbix repository for RHEL/CentOS, Debian, and Ubuntu.

## Requirements

This role only is needed/runs on RHEL and its derivatives, Debian, and Ubuntu.

## Role Variables

### RHEL/CentOS and Derivatives:

Available variables are listed below, optional parameters for overriding yum_repository defaults from (see tasks/main.yml for provided defaults):
https://docs.ansible.com/ansible/yum_repository_module.html#options

    repo_zabbix:
      param1: value
      ...

Every aspect of the yum repository definition can be changed with the above params variables. For example, you can remove the mirrorlist by setting it to null and use baseurl to set a local mirror repository of your choice.

### Debian and Ubuntu:

Available variables are listed below which can replace the defaults for Debian based distributions. The options for the key are found from the Ansible module http://docs.ansible.com/ansible/apt_key_module.html#id2, while the options for the repository itself follow that of http://docs.ansible.com/ansible/apt_repository_module.html#id3

    repo_zabbix_key:
      url: URL for repository GPG key
      id: GPG ID for Key
      state: present|absent

    repo_zabbix:
      url: URL for repository
      file: filename for repository.list
      repos:
        - repo1
        ...
      state: present|absent

## Dependencies

Debian/Ubuntu (on host  that executes module):
* python-apt

## Example Playbook

    - hosts: servers
      roles:
        - erenfro.repo-zabbix

## License

MIT / BSD

## Author Information

This role was created in 2016 by [Eric Renfro](https://linux-help.org/).

