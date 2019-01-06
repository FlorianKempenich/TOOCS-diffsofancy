[![Build Status](https://travis-ci.org/FlorianKempenich/ansible-role-diff-so-fancy.svg?branch=master)](https://travis-ci.org/FlorianKempenich/ansible-role-diff-so-fancy) [![Ansible Role](https://img.shields.io/ansible/role/23203.svg)](https://galaxy.ansible.com/FlorianKempenich/diff-so-fancy)

# Ansible role: `diff-so-fancy`
Install `diff-so-fancy` and set-up `git`

## Requirements
`NodeJs` and `npm` is required.
Also the path to the `node` executable needs to be set, see **Role Variables**

## Role Variables
**Set the `node_path` variable to the path of the `node` executable**

Before running this role set the `node_path` fact before running this role, or pass it as a variable
If `node` is already accessible with the default `PATH` environment variable, you can set `node_path` to an empty string.

If `node` was installed with `nvm`, check out this cool project of mine that will the the `node_path` fact for you: [FlorianKempenich.toocs_nodejs](https://galaxy.ansible.com/FlorianKempenich/toocs_nodejs)  
See below for examples.


## Example Playbook
Basic installation:
```
- hosts: sandbox
  tasks:
    - include_role:
        name: FlorianKempenich.diff-so-fancy
      vars:
        node_path: "{{ ansible_env.HOME }}/.nvm/versions/node/v6.11.4/bin"
```

If `node` is accessible with the default `PATH` variable, an empty `node_path` will do:
```
- hosts: sandbox
  tasks:
    - include_role:
        name: FlorianKempenich.diff-so-fancy
      vars:
        node_path: "" <--- Setting the variable is still required !!
```

Setting the path on a `nvm` installation with [FlorianKempenich.toocs_nodejs](https://galaxy.ansible.com/FlorianKempenich/toocs_nodejs):
```
- hosts: sandbox
  tasks:
    - include_role:
        name: FlorianKempenich.toocs_nodejs
        tasks_from: set-node-path-fact.yml
                      ^
                      ^--- This sets the `node_path` fact.
                           No more need to pass it as variable.

    - include_role:
        name: FlorianKempenich.diff-so-fancy
```

## License
MIT

## Author Information
Find out more about my work: [Florian Kempenich](https://floriankempenich.com)
