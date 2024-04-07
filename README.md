# Bootstraps for Linode instances

In a Linode `stackscript` clone this repo and do something with the contents.

## Linode stackscript

A simple skeleton for a Linode stackscript:

_for use with Almalinux 9_

```sh
#!/usr/bin/env bash
dnf install -y git ansible-core

git clone https://github.com/CantingCrew/linode-bootstraps.git

cat << EOF > /etc/ansible/ansible.cfg
[defaults]
verbosity=0
debug=false
callbacks_enabled = community.general.unixy
stderr_callback=unixy
stdout_callback=yaml
bin_ansible_callbacks = True
EOF


ansible-galaxy collection install community.general --timeout 10
ansible-galaxy collection install ansible.posix --timeout 10

ansible-playbook linode-bootstraps/ansible/update-localhost.yml

grep 'foreman::params' /var/log/foreman-installer/foreman.log > /root/foremanconfig.txt


```

# scripts

## Foreman deploy

Requires:
- 2 GB RAM
- AlmaLinux 9

# notes

ansible-collection-theforeman-foreman.noarch : The Foreman Project Ansible modules collection
ansible-collection-theforeman-operations.noarch : The Foreman Project Ansible operations collection

