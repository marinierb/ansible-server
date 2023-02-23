# Create some servers using ansible

## The playbooks

### - playbook-proxmox.yml
* remove proxmox subscription nag
* install some packages needed by ansible
* add proxmox non-prod software source
* comment out proxmox entreprise software source

### - playbook-media-vm.yml
* create the media server VM on proxmox

### - playbook-media-server.yml
* install nfs
* create filesystem mounts
* create nfs shares
* install transmission
* install expressvpn
* install mariadb (for kodi database)

### - playbook-pihole1-lxc.yml
* create a pihole container on proxmox

### - playbook-pihole2-docker-nuc.yml
* create a pihole docker container on desktop (as a backup)

### - playbook-portainer-docker-nuc.yml
* create a portainer docker container on desktop

## Running the playbooks

```
Secrets are stored 
```

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
