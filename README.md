pve_on_debian
=========

This role will install on Debian system (current Stretch)

Requirements
------------

Ansible (tested with 2.3.1.0)
Python (tested with 2.7.5)

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.
defaults/main.yml:
	ntp_pool: pool.ntp.org				# Pool of ntp-servers
	timzone: Europe/Moscow				# Default timezone
	debian_version: stretch				# Default release
	debian_repo: "http://mirror.yandex.ru/debian/"	# Default repo address
	add_pve-no-subscription: True			# Add pve-no-subscription repository
	disable_pve-enterprise: True			# Disable commercial repo
playbook vars( must be declared ):
	proxmox_ip			# ip address for new instance of Proxmox
	proxmox_mask			# network mask
	proxmox_gateway			# default gateway
	proxmox_physnet			# physical network for bridge (e.g. eth0)
	proxmox_bridge			# name of the virtual bridge (e.g. vmbr0)
	proxmox_hostname_fdqn		# fqdn for new Proxmox

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

```yaml
---
- hosts: proxmox_target
  gather_facts: true
  vars:
    - proxmox_physnet: eth0
    - proxmox_bridge: vmbr0
    - proxmox_ip: 192.168.1.253
    - proxmox_mask: 255.255.255.0
    - proxmox_gateway: 192.168.1.254
    - proxmox_hostname_fdqn: proxmox.testlab.lan
  vars_files:
    - users.yml
  roles:
    - proxmox_deploy
...
```

License
-------

GPL v 3.0

Author Information
------------------

https://tenhi.online
Tenhi adm@tenhi.ru
