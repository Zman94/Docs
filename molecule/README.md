# Molecule Docs

 Molecule is designed to aid in the development and testing of Ansible roles.

## Initializing

To keep environments clean, it is recommended to use a python virtualenvironment

```
$ virtualenv molecule_venv
$ source molecule_venv/bin/activate
```

Install molecule, ansible, and docker

```
$ pip install molecule ansible docker
```

Molecule can be customized during installation in several ways:
1. Driver
    * Vagrant (default)
        * Virtual machines for testing
    * Docker
        * Containers for testing
    * OpenStack
2. Providor
    * Virtualbox (default)
    * libvirt
    * VMWare Fusion
    * Parallels
3. Verifier
    * Testinfra (default)
    * Serverspec
    * Goss

We are going to use docker for the driver and defaults for the other options.

```
$ molecule init role --driver-name docker --role-name molecule-demo
$ cd molecule-demo
$ tree .
```

Molecule sets up a default file structure as shown above. We can test the initialization.

```
$ molecule test
```

## Example

Molecule checks `molecule/default/molecule.yml` for details about the platform we want to test. We can create a role in `task/main.yml` and Molecule runs the tests in `molecule/default/tests/test_default.py`.

We can create a sample role and test.

Add the following code to `task/main.yml`

```
---
- name: "Installing httpd service"
  yum:
    name: httpd
    state: installed
...
```

> All yml files start with --- and end with ...

Next, we add a test to `molecule/default/tests/test_default.py`.

```
import os

import testinfra.utils.ansible_runner

testinfra_hosts = testinfra.utils.ansible_runner.AnsibleRunner(
    os.environ['MOLECULE_INVENTORY_FILE']).get_hosts('all')


def test_hosts_file(host):
    f = host.file('/etc/hosts')

    assert f.exists
    assert f.user == 'root'
    assert f.group == 'root'


def test_package(Package):
    service = Package("httpd")
    assert service.is_installed
```

Now we can run the tests.

```
$ molecule test
```
