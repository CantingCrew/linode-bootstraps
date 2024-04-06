# Bootstraps for Linode instances

In a Linode `stackscript` clone this repo and do something with the contents.

## Linode stackscript

A simple skeleton for a Linode stackscript:

_for use with Almalinux 9_

```sh
#!/usr/bin/env bash
dnf install -y git ansible-core

git clone https://github.com/CantingCrew/linode-bootstraps.git

ansible-galaxy collection install community.general

ansible-playbook install-foreman.yml


```
