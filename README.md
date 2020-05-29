# irslackd

Install and configure irslackd on your system.

|Travis|GitHub|Quality|Downloads|
|------|------|-------|---------|
|[![travis](https://travis-ci.com/robertdebock/ansible-role-irslackd.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-irslackd)|[![github](https://github.com/robertdebock/ansible-role-irslackd/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-irslackd/actions)|[![quality](https://img.shields.io/ansible/quality/30532)](https://galaxy.ansible.com/robertdebock/irslackd)|[![downloads](https://img.shields.io/ansible/role/d/30532)](https://galaxy.ansible.com/robertdebock/irslackd)|

## Example Playbook

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: robertdebock.irslackd
```

The machine may need to be prepared using `molecule/resources/prepare.yml`:
```yaml
---
- name: Prepare
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.epel
    - role: robertdebock.git
    - role: robertdebock.ca_certificates
    - role: robertdebock.npm
```

For verification `molecule/resources/verify.yml` run after the role has been applied.
```yaml
---
- name: Verify
  hosts: all
  become: yes
  gather_facts: yes

  tasks:
    - name: check if connection still works
      ping:
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## Role Variables

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for irslackd

# The tcp port that irslackd should listen on.
irslackd_port: 6697

# The address that irslackd should bind to.
irslackd_address: 0.0.0.0

# Where to install irslackd.
irslackd_dest: /opt/irslackd

# The version of irslackd to install.
irslackd_version: dd994ef16a1a5245fa4f50fc4cf58e7397d51b93


# These settings are used for the SSL certificate.
irslackd_country: NL
irslackd_state: Utrecht
irslackd_location: Breukelen
irslackd_organization: Very little
irslackd_organizational_unit: IT Department
irslackd_common_name: "{{ ansible_fqdn }}"
```

## Requirements

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- robertdebock.bootstrap
- robertdebock.ca_certificates
- robertdebock.epel
- robertdebock.git
- robertdebock.npm
- robertdebock.service

```

## Context

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/irslackd.png "Dependency")

## Compatibility

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|el|8|
|debian|buster|
|fedora|31, 32|
|opensuse|all|
|ubuntu|focal, bionic|

The minimum version of Ansible required is 2.8 but tests have been done to:

- The previous version, on version lower.
- The current version.
- The development version.

## Exceptions

Some variarations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| amazonlinux:1 | SyntaxError: Use of const in strict mode. |
| amazonlinux:latest | SyntaxError: Unexpected identifier |
| centos:7 | SyntaxError: Unexpected identifier |
| alpine | Can't get the service to be idempotent. |
| debian:testing | The repository 'https://deb.nodesource.com/node_10.x bullseye Release' does not have a Release file. |

## Included version(s)

This role [refers to a version](https://github.com/robertdebock/ansible-role-irslackd/blob/master/defaults/main.yml) released by adsr on GitHub. Check the released version(s) here:
- [irslackd](https://github.com/adsr/irslackd/releases).

This version reference means a role may get outdated. Monthly tests occur to see if [bit-rot](https://en.wikipedia.org/wiki/Software_rot) occured. If you however find a problem, please create an issue, I'll get on it as soon as possible.
## Testing

[Unit tests](https://travis-ci.com/robertdebock/ansible-role-irslackd) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-irslackd/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

## License

Apache-2.0


## Author Information

[Robert de Bock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).
