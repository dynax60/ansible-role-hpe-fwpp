# Install latest firmware on HPE servers

## Install

```
mkdir -p roles && cd roles
git clone https://github.com/dynax60/ansible-role-hpe-fwpp.git
```

## Example of host_vars/node1.yml

This is an example how to install firmware on server node1 and track it

** host_vars/node1.yml **

```yaml
---
hpe_fwpp_packages:
  - firmware-ilo5
  - firmware-system-u31
  - firmware-nic-intel
  - firmware-smartarray-f7c07bdbbd
  - firmware-hdd-f693ccc138-HPG3
```

** install-hpe-sdr.yml: **

```yaml
#!/usr/bin/env ansible-playbook
---
- hosts: "{{ inventory | default('centos') }}"
  become: yes
  roles:
    - role: ansible-role-hpe-fwpp
```

Run:

```
chmod +x ./install-hpe-sdr.yml
./install-hpe-sdr.yml
