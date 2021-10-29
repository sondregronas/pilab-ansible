# pilab-ansible

Deployment of Raspberry Pi devices in a School Lab environment. - Mainly just figuring out Ansible.

Tested on Raspberry Pi 4 (2GB) running a clean install of Raspberry Pi OS (32-bit)

---
### What it does
- Currently updates Raspbian from buster to bullseye
- Changes the admin password on user pi
- Disables autologin to user pi, login prompt is instead selected
- Updates aptitude
- Installs gcc-8-base, this is required for the transition from buster to bullseye
- Does a full upgrade
- Installs php-mysql, php, mariadb-server (for later use)
- Also installs cockpit (for remote management, you will need to setup cockpit on your admin pi aswell)
- Performs a reboot

### Steps to setup
 - Enable SSH on all pis
 - Login as root on admin pi
 - `ssh-copy-id pi@host`
 - Authorize ssh-keys to root:
 - `ansible -m shell -a 'sudo mkdir /root/.ssh' -u pi all`
 - `ansible -m shell -a 'sudo cp .ssh/authorized_keys /root/.ssh/authorized_keys' -u pi all`

### The goal
The goal is simply to save time when setting up / resetting pi's in a classroom environment. The main thing to figure out still is evenly distributing user accounts (for the students) on all the hosts in the inventory.
