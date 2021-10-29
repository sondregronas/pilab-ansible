# pilab-ansible

Deployment of Raspberry Pi devices in a School Lab environment.

Tested on Raspberry Pi 4 (2GB) running a clean install of Raspberry Pi OS (32-bit)

---
### What it does
- Currently updates Raspbian from buster to bullseye
- Changes the admin password on user pi
- Changes the hostname of the pis based off of variable in inventory.ini
- Creates users on the pi based off the hostname
- Disables autologin to user pi, login prompt is instead selected
- Updates aptitude
- Installs gcc-8-base, this is required for the transition from buster to bullseye
- Does a full upgrade
- Installs php-mysql, php, mariadb-server (for later use)
- Also installs cockpit (for remote management, you will need to setup cockpit on your admin pi aswell)
- Performs a reboot

### Steps to setup
 - `cp example.config.yml config.yml` to create the config file, adjust to your liking
 - `cp example.inventory.ini inventory.ini` to create the hosts file, adjust to your liking
 - Enable SSH on all pis
 - Login as root on admin pi
 - `ssh-copy-id pi@host`
 - Authorize ssh-keys to root:
 - `ansible -m shell -a 'sudo mkdir /root/.ssh' -u pi all`
 - `ansible -m shell -a 'sudo cp .ssh/authorized_keys /root/.ssh/authorized_keys' -u pi all`

### The goal
The goal is simply to save time when setting up / resetting pi's in a classroom environment.
