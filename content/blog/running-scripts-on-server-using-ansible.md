---
title: Running Shell Scripts on Server Using Ansible
date: 2020-08-07T12:02:56
excerpt: This blog is about how to run script on the server(s) using Ansible. You need to follow some various steps to run the script on hosts. It is very useful and helpful for an IT Admin to handle thousands of hosts using one command. You need to configure your hosts as well as your local machine from which you want to run the command.
---

This blog is about how to run a script on the server(s) using Ansible. You need to follow some various steps to run the script on hosts. It is very useful and helpful for a IT Admin to handle thousands of hosts using one command. You need to configure your hosts as well as your local machine from which you want to run the command.

To run the script from your machine to host(s) you need to create a user for Ansible or change the configuration for the existing users. To see this in detail you can refer to this [blog](https://thejsdeveloper.wordpress.com/2020/08/06/getting-started-with-ansible/ ). Let’s see in brief what are the changes needed to run the script.


- You need to allow no password for the user in the host. To do this run: 
```
- $ sudo visudo
- Add the line `<user> ALL=(ALL:ALL) ALL`
```
- You need to have a passwordless entry for the user in order to use Ansible, for that you need to follow these commands.
```
- $ ssh-keygen
- $ ssh-copy-id -i ~/.ssh/id_rsa.pub <user>@<host>

- Now try logging in to the host to check whether it needs a password or not, for that run:
- $ ssh <user>@<host>
```

This will log you into the host without a password. Otherwise, Ansible will show the error of permission denied.

## Running the script on the Host machine

1. Create a directory in which we will place all the files related to Ansible.
```
$ mkdir Ansible && cd Ansible
```
<br />

2. Create a shell script that you want to run. Note that the given script is of the bash shell.
```
$ vim create-file.sh
```
<br />

3. Put the content following content in create-file.sh
```
#!/bin/bash
touch /tmp/ansible_script_file
```
<br />

4. Create a configuration file for Ansible and paste the given content.
```
$ vim ansible.cfg

# Paste the below content

[defaults]
inventory = ./inventory
retry_files_enabled = False
[ssh_connection]
pipelining = True
```
<br />

5. Create a file inside the directory ./group_vars/ubuntu.yml. If you have more than one host you need to create a different file for each host to specify some detail in it. The content inside the file will be:
```
---
ansible_user: <username>
ansible_python_interpreter: /usr/bin/python3
---
```
*ansible_usern* => User for ansible on host machine <br />
*ansible_python_interpreter* => You need to define the path of python interpreter if it is by default other than  `/usr/bin/python` <br />

6. Create a file named ‘hosts’ inside the ./inventory directory. The content for the host's file will be:
```
[ubuntu]
ubuntu_host ansible_host=<host>
```
In this file *ubuntu_host* is the hostname like this there could be multiple hostnames in this file. 

7. Now create the Playbook for Ansible. In this file, all the instructions will be given to Ansible.

```
$ vim create-file-playbook.yml

# Content for this file:

---
- name: Transfer and execute a script
hosts: "*" # It will match all the hosts in you ./inventory/hosts file
tasks:
- name: Copy shell script
copy: src=/home/<local-machine-username>/ansible/file-create.sh dest=/opt/ansi mode=0777
- name: Executing shell script
command: sh /home/<username>/create-file.sh
---
```
<br />

8. Your directory structure is going to look something like this <br />

![Directory Structure](https://thejsdeveloper.files.wordpress.com/2020/08/screenshot_2020-08-07_15-52-47.png)
<br />

9. You are ready to rock. Now run the playbook command of Ansible to run the playbook.
```
$ ansible-playbook create-file-playbook.yml
```
<br />

10. You will see output like this…

![Directory Structure](https://thejsdeveloper.files.wordpress.com/2020/08/screenshot_2020-07-29.png?w=1024) <br />


### That’s all for it. I hope this helped you to solve your problem. Have a nice day!