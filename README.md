# Ansible playbooks to manage Banana Pi clusters

This repository contains a set of Ansible playbooks that help to set up and manage a Banana Pi cluster.

## How to run?

Install Ansible on a control node and define an inventory (**/etc/ansible/hosts**). For example:

```
[bpies_ips]
192.168.1.104		ansible_user=pi		hostname=bpi01
192.168.1.100		ansible_user=pi		hostname=bpi02
192.168.1.103		ansible_user=pi		hostname=bpi03
192.168.1.101		ansible_user=pi		hostname=bpi04
192.168.1.105		ansible_user=pi		hostname=bpi05
192.168.1.102		ansible_user=pi		hostname=bpi06

[bpies]
bpi[01:06].local	ansible_user=pi

[bpies_manager]
bpi01.local			ansible_user=pi

[bpies_workers]
bpi[02:06].local	ansible_user=pi
```

Run a playbook as follows:

```bash
ansible-playbook some-playbook.yml --ask-pass
```

Or:

```bash
ansible-playbook some-playbook.yml --ask-pass --ask-become-pass
```

## Configuring

Change the target group names (the default are `bpies`, `bpies_manager’, and `bpies_workers`) in the **.yml** files before running a playbook if needed.

## Available playbooks

* **configure-hosts.yml**: Sets host names
* **ping.yml**: Pings all the nodes
* **upgrade.yml**: Updates and upgrades the nodes
* **docker-swarm**: Installs Docker and creates a Docker Swarm cluster
* **rm-docker-swarm**: Deletes the Docker Swarm cluster
* **reboot.yml**: Reboots all the nodes
* **shutdown.yml**: Shuts down all the nodes
* **temperature.yml**: Prints the temperature of each machine
