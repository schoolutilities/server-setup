# Introduction to our sever setup with ansible

This is a collection of ansible playbooks to setup a server. It is based on [ansible best practices](https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html) and [ansible galaxy](https://galaxy.ansible.com/).

## What is ansible?

Ansible is a configuration management tool. It is used to setup a server. It is based on the concept of playbooks. A playbook is a list of tasks.

# How to use this playbooks

## Prerequisites

- Ansible is installed on your machine
- On windows you have to use WSL2 to run ansible
- Have an ssh key generated on your WSL2 machine, it can be generated with the `ssh-keygen` command, and the public key pasted in the authorized_keys file on the server, this file is usually located in the .ssh folder in the home directory of the user you want to connect with

### Add config files

You have to create the inventory config file which has no file extension and contains the ip address where the playbooks should run in each line. The file should be located in the root directory of this project.

In addition to that you need to create the ansible.cfg file where you can copy the content from the example file and edit the username and the path to the ssh key on your local machine.

## Run the playbooks

To run the playbooks you have to run the following command:

```bash
ansible-playbook playbook.yml
```

### Run the playbooks in the right order

1. install_packages.yml - installs all the packages needed for the other playbooks
2. install_npm.yml - installs npm and nodejs
3. install_docker.yml - installs docker and docker-compose
4. install_portainer.yml - installs portainer to manage all docker container on the server
5. install_proxy.yml - installs nginx as a reverse proxy to route all traffic to the right container
