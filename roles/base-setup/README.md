# Ansible Role: Base Setup

This role performs the base setup of an operating system, excluding system updates. It creates system groups, system
users, installs base packages, and configures the UFW firewall.

**Note: This role should be used with caution, as it modifies system-level configurations. There are no tests provided
with this role.**

## Requirements

This role requires Ansible to be installed on the control node. It has been tested on the following operating systems:

- Ubuntu 20.04 LTS

## Role Variables

This role has the following variables:

### `system_groups`

A list of system groups to create. The default value is:

- `name`: sudo
- `name`: devops

### `system_users`

A list of system users to create. Each user can define the following keys:

- `name`: the username
- `groups`: a list of groups the user should belong to (in addition to the `devops` group)
- `ssh_key_path`: the path to the user's public SSH key file

The default value is an empty list.

### `packages`

A list of base packages to install. The default value is:

- `vim`: sudo
- `curl`: devops
- `wget`: devops
- `ufw`: devops
- `htop`: devops
- `net-tools`: devops

## Example Playbook

```yaml
- hosts: all
  vars:
    system_groups:
      - group1
      - group2
    system_users:
      - name: user1
        ssh_key_path: /path/to/user1/key.pub
        groups:
          - group1
      - name: user2
        ssh_key_path: /path/to/user2/key.pub
        groups:
          - group2
      - name: user3
        ssh_key_path: /path/to/user3/key.pub
    packages:
      - vim
      - curl
      - wget
      - ufw
      - htop
      - net-tools
      - net-tools
  roles:
    - base-setup
```

In this example, the system_groups variable is defined as a list of group1 and group2, and the system_users variable is
defined as a list of three users. user1 belongs to group1, user2 belongs to group2, and user3 belongs only to the devops
group by default.

Note that you can also define the packages variable in your playbook to install additional packages beyond the base
packages defined in the role.

## License

This role is licensed under the terms of the MIT License. This means that you are free to use, copy, modify, merge,
publish, distribute, sublicense, and/or sell copies of the role, as long as the original copyright notice and license
are included.

The MIT License is a permissive open-source license that places very few restrictions on how the code can be used. It is
often used for software that is meant to be shared and used by others, and it allows for maximum flexibility in how the
code is distributed and used.