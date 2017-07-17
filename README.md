
ansible-role-virtualbox
=======================

```shell
[![Build Status](https://travis-ci.org/cjsteel/ansible-role-virtualbox.svg?branch=master)](https://travis-ci.org/cjsteel/ansible-role-virtualbox)
```

An ansible role for installing, reinstalling, removing and purging virtualbox

## Procedure

```shell
sudo apt remove virtualbox
## ubuntu xenial
# deb http://download.virtualbox.org/virtualbox/debian xenial contrib
## debian 8 jesse
#deb http://download.virtualbox.org/virtualbox/debian jessie contrib
```

### Additional notes:

#### VirtualBox 5.1 was released on July 12, 2016

- increased Linux Integration, [DKMS](https://www.linuxbabe.com/virtualbox/how-to-install-virtualbox-guest-additions-on-ubuntu-step-by-step) is no longer needed
- improved multimedia support
- a new bug reporting helper tool
- a new NVMHCI storage controller for emulating NVMe (NVM Express) devices, aka, flash storage
- better support for USB devices and multi-channel audio
- significantly improved performance when running VMs with multi-CPU
- improved systemd integration

## Requirements

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.


## Variables

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.


## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook


### Minimalist
You probably want this in almost all cases. The relies on defaults/main.yml value for the var **ensure_virtualbox**.

```shell
---
- hosts: virtualbox
  become: true
  gather_facts: true
  roles:
    - virtualbox
```

#### Overide var in default/main.yml for all hosts in inventory

```yaml
- hosts: virtualbox
  become: true
  gather_facts: false
  vars:
    - virtualbox_state: 'absent'
  roles:
    - virtualbox
```

#### Overide default/main.yml by passing value for ensure_virtualbox via the role

    - hosts: all
      become: true
      gather_facts: false
      roles:
        - { role: "virtualbox", virtualbox_state: 'present' }


## Example Command

```shell
ansible-playbook -i inventory/dev site.yml --ask-become-pass --limit workstation_001
```

## Role Testing

### Locally using vagrant

```shell
mkdir .vagrant/synced
vagrant up
vagrant ssh -- -X
```

### Check via terminal

```shell
vboxmanage --version
```
Output

### Via script

```shell
#!/bin/bash
echo $(vboxmanage --version)
```

### vi GUI

```shell
which virtualbox
```

```shell
virtualbox
```

Check the version.

Example:

```shell
VirtualBox Graphical User Interface
Version 5.1.22 r115126 (Qt5.5.1)
Copyright © 2017 Oracle Corporation and/or its affiliates. All rights reserved.
```


```shell
exit
vagrant destroy # if you are done testing
```


License
-------

* [MIT](https://opensource.org/licenses/MIT)

![OSI Logo](https://opensource.org/files/osi_logo_100X133_90ppi_0.png "OSI Logo")


Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
