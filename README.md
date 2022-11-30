# Ansible playbooks to manage Banana Pi clusters

This repository contains a set of Ansible playbooks that help to set up and manage a Banana Pi cluster.

## How to run?

Install Ansible on a control node and define an inventory (**/etc/ansible/hosts**). For example:

```
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

* **ping.yml**: Pings all the nodes
* **new-cluster.yml**: Updates the nodes
* **shutdown.yml**: Shuts down all the nodes
* **docker-swarm**: Configures the Docker Swarm cluster
* **temperature.yml**: Prints the temperature of each machine
