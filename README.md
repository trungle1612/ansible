# Install ansible
- Three are many ways to install ansible, but the easiest way is installing with `pip`
```
$ sudo pip install ansible
```
Or you can read at this [link](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
# Ansible: Ruby on Rails Server
Use this ansible playbook to setup a fresh server with the following components:

* Nginx
* Certbot (Let's Encrypt)
* MySQL
* Memcached
* Redis
* Sidekiq
* Monit (to keep Puma and Sidekiq runnig)
* rbenv
* Directories to deploy Rails with Capistrano and Puma App Server (see below)
* Swapfile (useful for small DO instances)
* Locales
* Tools (tmux, vim, htop, git, wget, curl etc.)
* java
* elastic-search

## Prerequisites & Config

1. Rename ```hosts.example``` to ```hosts``` and modify the contents.
2. Rename ```group_vars/all.example``` to ```group_vars/all``` and modify the contentes.

	There are a bunch of things you can set in ```group_vars/all```. Don't forget to add your host address to ```hosts```.

## Install Playbook

Run ```ansible-playbook site.yml -i hosts```.

## Rails Setup
This is just a loose guideline for what you need to deploy your app with this playbook and server config. Please keep in mind, that you need to modify some values depending on your setup (**especially passwords and paths!**)

### Define
- name: This tag specifies the name of than Ansible playbook. As in what this playbook will be doing. Any logical name can be given to the playbook.
- hosts: This tag specifies the lists of hosts group against which we want to run the task. The hosts field/tag is mandatory. It tells Ansible which hosts to run the listed tasks. The tasks can be run on the same machnie or on a remote machine. One can run the tasks on multiple machines and hence hosts tag can have a group of hosts's entry as well.
- vars: Vars tag lets you define the variables which you can use in your playbook. Usage is similar to variables in any progarmming language.
- tasks: All playbooks should contain tasks or a list of task to be executed. Tasks are a list of actions one needs to perform.
- Roles: Roles provide a framwork for fully independent, or interdependent collections of variables, tasks, files, templates, and modules.
- variables: In order to use and assign a value to a variable and use that anywhere in the playbook.
- keywords:
  + block
  + name
  + action
  + register
  + always
  + msg
