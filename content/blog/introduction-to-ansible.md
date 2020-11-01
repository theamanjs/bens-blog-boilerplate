---
title: Getting Started With Ansible
date: 2020-08-06T12:02:56
excerpt: Ansible is the simplest way to automate apps and IT infrastructure. Application Deployment + Configuration Management + Continuous Delivery.
---

Ansible is the simplest way to automate apps and IT infrastructure. Application Deployment + Configuration Management + Continuous Delivery.


## Prerequisite for Ansible

- You need Python 2 (version 2.6 or later) or Python 3 (version 3.5 or later).


## Installation Steps:

```
1. $ sudo apt update
2. $ sudo apt install software-properties-common
3. $ sudo apt-add-repository --yes --update ppa:ansible/ansible
4. $ sudo apt install ansible
```

## Configuring and using Ansible
In this configuration there are two new terms. One is Managed node which is the remote server that is managed by Ansible. Other one is Control node which is the machine from which command will be given to Ansible. There are some steps to use Ansible which are written below:

1. Log onto the control and managed node to add a user and set a password. Use the command:
```
useradd <username>
passwd <username>
```
<br />

2. On the managed node, we need to ensure our Ansible user can utilize the sudo command without a password. Run command:
```
$ sudo visudo
admin ALL=(ALL) NOPASSWD: ALL

# Add the above line to the end of file.
```
<br />

3. In the control node we need SSH key pair, for that run:
```
$ ssh-keygen

Copy the public key to our managed node, run:
 
$ ssh-copy-id <host>

```
<br />

4. Create an Ansible Inventory. Before that make sure you are logged onto the Control node as the same user you created.
```
$ vim /home/${whoami}/inventory
Type the <host> in the file and save. Eg. node.theamanjs.com
```
<br />

5. On control node, create an Ansible Playbook.
```
$ vim /home/${whoami}/install-nginx.yml
```
<br />

6. Write the below content in the yaml file to create the playbook.

![nginx-playbook-ansible](https://thejsdeveloper.files.wordpress.com/2020/08/nginx-playbook-ansible.png) <br />

7. After the yaml file is created now run the Playbook with Ansible using the following command:
```
$ ansible-playbook -i /home/${whoami}/inventory /home/${whoami}/install-nginx.yml
```
<br />

### I hope it helped you to learn something new!!!