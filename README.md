irslackd
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-irslackd.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-irslackd)

Provides a self-hosted IRC gateway to Slack.

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-irslackd) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-irslackd/issues)

To test this role locally please use [Molecule](https://github.com/metacloud/molecule):
```
pip install molecule
molecule test --scenario-name fedora-latest
```
There are many scenarios available, please have a look in the `molecule/` directory.


Context
--------
This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/irslackd.png "Dependency")

Requirements
------------

- A system installed with required packages to run Ansible. Hint: [bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap).
- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the last 3 release of Ansible.)
- Have epel for RHEL systems installed. Hint: [epel](https://galaxy.ansible.com/robertdebock/epel)
- Have npm installed. Hint: [npm](https://galaxy.ansible.com/robertdebock/npm)

Role Variables
--------------

irslackd_dest: Where to place the downloaded irslackd [default: /opt/irslackd]
irslackd_version: The version (either tag or commit hash) to install.
irslackd_package_state: What to do with packages installed by this role. Either present, absent or latest. [defaut: present]
irslackd_country: What country to use to generate the SSL certificate. [default: NL
irslackd_state: What country to use to generate the SSL certificate. [default: Utrecht]
irslackd_location: What country to use to generate the SSL certificate. [default: Breukelen]
irslackd_organization: What country to use to generate the SSL certificate. [default: Very little]
irslackd_organizational_unit: What country to use to generate the SSL certificate. [default: IT Department]
irslackd_common_name: What country to use to generate the SSL certificate. [default: "{{ ansible_fqdn }}"]

Dependencies
------------

- None known.

Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.4|ansible 2.5|ansible 2.6|ansible 2.7|ansible devel|
|------------|-----------|-----------|-----------|-----------|-------------|
|alpine-edge|yes|yes|yes|yes|yes|
|alpine-latest|yes|yes|yes|yes|yes|
|archlinux|yes|yes|yes|yes|yes|
|centos-6|yes|yes|yes|yes|yes|
|centos-latest|yes|yes|yes|yes|yes|
|debian-latest|yes|yes|yes|yes|yes|
|debian-stable|yes|yes|yes|yes|yes|
|fedora-latest|yes|yes|yes|yes|yes|
|fedora-rawhide|yes|yes|yes|yes|yes|
|opensuse-leap|yes|yes|yes|yes|yes|
|opensuse-tumbleweed|yes|yes|yes|yes|yes|
|ubuntu-artful|yes|yes|yes|yes|yes|
|ubuntu-latest|yes|yes|yes|yes|yes|

Example Playbook
----------------

```
---
- name: irslackd
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.epel
    - role: robertdebock.npm
    - role: robertdebock.irslackd
```

To install this role:
- Install this role individually using `ansible-galaxy install robertdebock.irslackd`

Sample roles/requirements.yml: (install with `ansible-galaxy install -r roles/requirements.yml
```
---
- name: robertdebock.bootstrap
- name: robertdebock.epel
- name: robertdebock.npm
- name: robertdebock.irslackd
```

License
-------

Apache License, Version 2.0

Author Information
------------------

[Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
