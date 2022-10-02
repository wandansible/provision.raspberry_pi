Ansible role: Provision - Raspberry Pi
======================================

Provision a Raspberry Pi that already has Raspberry Pi OS
installed, contains a provision user with sudo permissions,
and has sshd installed and running. If using SSH public key
authentication then the provision user's public key must be
included in their authorized keys file.

Requirements
------------

This role depends on the [base provision role](https://github.com/wandansible/provision).

Role Variables
--------------

```
ENTRY POINT: main - Provision Raspberry Pi

        Provision a Raspberry Pi that already has Raspberry Pi OS
        installed, contains a provision user with sudo permissions,
        and has sshd installed and running. If using SSH public key
        authentication then the provision user's public key must be
        included in their authorized keys file.

OPTIONS (= is mandatory):

- raspi_kernel_restart
        If true, restart into new kernel during provision
        [Default: True]
        type: bool

- raspi_memory_split_megabytes
        Amount of shared memory (in megabytes) to dedicate to the GPU
        [Default: 16]
        type: int
```

Installation
------------

This role can either be installed manually with the ansible-galaxy CLI tool:

    ansible-galaxy install git+https://github.com/wandansible/provision,main,wandansible.provision
    ansible-galaxy install git+https://github.com/wandansible/provision.raspberry_pi,main,wandansible.provision.raspberry_pi
     
Or, by adding the following to `requirements.yml`:

    - name: wandansible.provision
      src: https://github.com/wandansible/provision
    - name: wandansible.provision.raspberry_pi
      src: https://github.com/wandansible/provision.raspberry_pi

Roles listed in `requirements.yml` can be installed with the following ansible-galaxy command:

    ansible-galaxy install -r requirements.yml

Example Playbook
----------------

    - hosts: all
      roles:
         - role: wandansible.provision.raspberry_pi
           become: true
           vars:
             root_password: "hunter2"
