# Create some servers using ansible

![GitHub last commit](https://img.shields.io/github/last-commit/marinierb/ansible-server)

## The playbooks

### playbook-proxmox.yml
* remove proxmox subscription nag
* install some packages needed by ansible
* add proxmox non-prod software source
* comment out proxmox entreprise software source

### playbook-media-vm.yml
* create the media server VM on proxmox
* attach disks
* set hostname
* configure static ip

### playbook-media-server.yml
* install nfs server
* create filesystem mounts
* create nfs shares
* install transmission
* install expressvpn
* install mariadb (for kodi database)

### playbook-pihole1-lxc.yml
* create a pihole container on proxmox

### playbook-pihole2-docker-nuc.yml
* create a pihole docker container on desktop (as a backup)

### playbook-portainer-docker-nuc.yml
* create a portainer docker container on desktop

## Running the playbooks

**Note**: Secrets are stored in **group_vars/all/vault.yml** and the password in **.vaultpass**, both of which are in the **.gitignore**.

1. Install some required external roles (for pihole and mariadb)

        install-roles.sh

1. Run the desired helper, e.g.

        an-media-vm

1. Or run individual role within a playbook, .e.g

        an-media-vm clone

## Tooling

### .make_helpers

* Creates a helper for each existing playbook
* Also creates the bash completion script for each helper

### checkRolesUsed

* Lists each role and the playbooks that use it
* Identifies unused roles
