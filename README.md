ansible.role.virtualbox
=======================

[![Build Status](https://travis-ci.org/cjsteel/ansible-role-virtualbox.svg?branch=master)](https://travis-ci.org/cjsteel/ansible-role-virtualbox)


An ansible role for installing, reinstalling, removing and purging virtualbox

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

#### Minimalist
You probably want this in almost all cases. The relies on defaults/main.yml value for the var **ensure_virtualbox**.

    - hosts: all
      become: true
      roles:
        - virtualbox

#### Overide var in default/main.yml for all hosts in inventory

    - hosts: all
      become: true
      gather_facts: false
      vars:
        - ensure_virtualbox: uninstalled
      roles:
        - virtualbox

#### Overide default/main.yml by passing value for ensure_virtualbox via the role

    - hosts: all
      become: true
      gather_facts: false
      roles:
        - { role: "virtualbox", ensure_virtualbox: "installed" }

Example Command
---------------

    ansible-playbook -i inventory/dev site.yml --ask-become-pass

License
-------

* [MIT](https://opensource.org/licenses/MIT)

![OSI Logo](https://opensource.org/files/osi_logo_100X133_90ppi_0.png "OSI Logo")


Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
