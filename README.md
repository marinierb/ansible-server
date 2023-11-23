# Ansible Media Server Setup

![GitHub last commit](https://img.shields.io/github/last-commit/marinierb/ansible-server)

## Configure my media server

1. Install Manjaro Gnome on /dev/sda
1. Make sure the OS is up to date

        pamac update

1. Set static IP

        sudo nmcli con mod "Wired connection 1" \
          ipv4.addresses "192.168.0.11/24" \
          ipv4.gateway "192.168.0.1" \
          ipv4.dns "192.168.0.2" \
          ipv4.dns-search "home.arpa" \
          ipv4.method "manual"

1. Configure and test **ssh**
1. Run playbook, which will:
   * clean up some stuff
   * enable AUR
   * configure some stuff (shell, swap, power settings)
   * create filesystem mounts (two nvme drives with existing data are used)
   * install nfs server
   * create nfs shares
   * install mariadb (for kodi database)
   * install expressvpn
   * install transmission

## Running the playbook

**Note**: Secrets are stored in **group_vars/all/vault.yml** and the password in **.vaultpass**, both of which are in the **.gitignore**.

1. Run the helper

        an-server

1. Or run individual role by specify a tag from the playbook .e.g

        an-server db

## Tooling

### .make_helpers

* Creates a helper for each existing playbook
* Also creates the bash completion script for each helper

### checkRolesUsed

* Lists each role and the playbooks that use it
* Identifies unused roles
