# Ansible-role-virtualbox examples README.md

## ansible.cfg

Ansible config points to our inventory file.

### content example:

    [defaults]
    hostfile       = inventory/dev

## inventory/dev

### Example of contents

    [virtualbox]
    all

## roles/virtualbox is a sym link to our virtualbox role.

## site.yml

### site.yml content example

    ---
    - hosts: all
      become: true
      roles:
        - { role: "virtualbox" }


## Vagrantfile

a very minimal Vagrantfile, it should just work.

### Content example

    # -*- mode: ruby -*-
    # vi: set ft=ruby :
    
    VAGRANTFILE_API_VERSION = "2"
    
    Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
      config.vm.box = "ubuntu/trusty64"
    
      config.vm.provision "ansible" do |ansible|
        ansible.playbook = "site.yml"
        ansible.sudo = true
      end
    end

