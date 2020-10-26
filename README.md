Ansible Role: ctop
==================

[![Build Status](https://travis-ci.com/gantsign/ansible_role_ctop.svg?branch=master)](https://travis-ci.com/gantsign/ansible_role_ctop)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-gantsign.ctop-blue.svg)](https://galaxy.ansible.com/gantsign/ctop)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/gantsign/ansible_role_ctop/master/LICENSE)

Role to download and install [ctop](https://ctop.sh) the top-like interface for
container metrics. View CPU, RAM and network I/O for your Docker containers at
a glance from your terminal.

Requirements
------------

* Ansible >= 2.8

* Linux Distribution

    * Debian Family

        * Debian

            * Jessie (8)
            * Stretch (9)

        * Ubuntu

            * Xenial (16.04)
            * Bionic (18.04)

    * RedHat Family

        * CentOS

            * 7

        * Fedora

            * 31

    * SUSE Family

        * openSUSE

            * 15.1

    * Note: other versions are likely to work but have not been tested.

* Docker (already installed)

Role Variables
--------------

The following variables will change the behavior of this role (default values
are shown below):

```yaml
# ctop version number
ctop_version: '0.7.4'

# SHA256 sum for the ctop redistributable
ctop_redis_sha256sum: '43d41ed0b2bb5cfc2aaa7b7fdd2d6cb515f6d88adc40ff40e3ec1f560e8a4413'

# Directory to store files downloaded for ctop
ctop_download_dir: "{{ x_ansible_download_dir | default(ansible_env.HOME + '/.ansible/tmp/downloads') }}"
```

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - role: gantsign.ctop
```

Tab Completion for Zsh
----------------------

### Using Ansible

We recommend using the
[gantsign.antigen](https://galaxy.ansible.com/gantsign/antigen) role to enable
tab completion for ctop (this must be configured for each user).

```yaml
- hosts: servers
  roles:
    - role: gantsign.ctop

    - role: gantsign.antigen
      users:
        - username: example
          antigen_bundles:
            - name: ctop
              url: gantsign/zsh-plugins
              location: ctop
```

### Using Antigen

If you prefer to use [Antigen](https://github.com/zsh-users/antigen) directly
add the following to your Antigen configuration:

```bash
antigen bundle gantsign/zsh-plugins ctop
```

More Roles From GantSign
------------------------

You can find more roles from GantSign on
[Ansible Galaxy](https://galaxy.ansible.com/gantsign).

Development & Testing
---------------------

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing; the role is unit tested using
[Testinfra](http://testinfra.readthedocs.io/) and
[pytest](http://docs.pytest.org/).

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)

Because the above can be tricky to install, this project includes
[Molecule Wrapper](https://github.com/gantsign/molecule-wrapper). Molecule
Wrapper is a shell script that installs Molecule and it's dependencies (apart
from Linux) and then executes Molecule with the command you pass it.

To test this role using Molecule Wrapper run the following command from the
project root:

```bash
./moleculew test
```

Note: some of the dependencies need `sudo` permission to install.

License
-------

MIT

Author Information
------------------

John Freeman

GantSign Ltd.
Company No. 06109112 (registered in England)
