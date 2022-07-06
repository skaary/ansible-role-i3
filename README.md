# Ansible Role: i3
[![CI](https://github.com/skaary/ansible-role-i3/actions/workflows/ci.yml/badge.svg?branch=main&event=push)](https://github.com/skaary/ansible-role-i3/actions?query=workflow%3Ci)

An Ansible Role that installs [i3](https://i3wm.org/) or [i3-gaps](https://github.com/Airblader/i3) on Linux.

## Installation

Download the role directly from git by typing into your terminal:

```bash
$ ansible-galaxy install git+https://github.com/skaary/ansible-role-i3.git
```

or

```bash
$ ansible-galaxy install git+https://github.com/skaary/ansible-role-i3.git,,i3
```

to change the installed role name from _ansible-role-i3_ to just _i3_.

Alternatively, install the role via a _requirements.yml_ file, e.g. when installing multiple roles at once. See [ansible galaxy documentation](https://galaxy.ansible.com/docs/using/installing.html#installing-multiple-roles-from-a-file) for more information.

## Role variables
| Variable name        | Default value        | Description                                                                                           |
| -------------------- | -------------------- | ----------------------------------------------------------------------------------------------------- |
| `i3`                 | `false`              | Set to true to only install the default i3 package from the default apt repository. False by default. |
| `i3_gaps_ppa`        | `true`               | Set to true to install i3-gaps from the repolith ppa. True by default.                                |
| `i3_extras`          | `true`               | Set to true to install extra packages defined in the variable `i3_extra_packages`. True by default.   |
| `i3_extras_packages` | `picom, dunst, rofi` | By default, the packages `picom`, `dunst`, and `rofi` will be installed in addition to i3-gaps.       |

## Example playbook

```yaml
- hosts: all
  roles:
    - ansible-role-i3
```

## Testing the role

### Vagrant

Vagrant can be used to test the role in order to graphically see it working in a virtual machine. Make sure Vagrant and VirtualBox are installed:

```bash
$ sudo apt install vagrant virtualbox
```

Use the following commands to run vagrant and boot up the virtual machine:

```bash
$ cd tests
$ vagrant up
```

Use `vagrant destroy` after you are done testing to delete the virtual machine. For more information about Vagrant and its commands, see the [Vagrant documentation](https://www.vagrantup.com/docs/cli).

### Molecule with Docker

Molecule can be used to test the role with a docker container. Make sure Molecule is installed:

```bash
$ python3 -m pip install --user "molecule[docker]"
```

Use the following commands to run Molecule in order to create the docker container and access the created container:
```bash
$ molecule converge && molecule login
```

For more information on how to use Molecule please consult the [Molecule documentation](https://molecule.readthedocs.io/en/latest/getting-started.html).

> Note: Python and Docker are required for the use of molecule. For more information, see [Molecule installation](https://molecule.readthedocs.io/en/latest/installation.html).

## License

MIT / BSD
