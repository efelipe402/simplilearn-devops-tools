# creating httpd server

let's setup and deploy an http server, for the ansible clients.


1. Install ansible in your machine.
https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installation-guide
https://docs.ansible.com/ansible/latest/reference_appendices/config.html#ansible-configuration-settings


2. Edit the ansible hos depending on the machine OS for linux will be
/etc/ansible/hosts or for mac OS installed by brew, you can create a folder at the root the of the user 
/users/user01/ansible

inside ansible the files will be 

hosts: a file
ansible.cfg: ansible-config init --disabled > ansible.cfg
roles: a folder

add the user machine ip and the username and password if required at the [ansible_clients] scope
# This is the default ansible 'hosts' file.
#
# It should live in /etc/ansible/hosts
#
#   - Comments begin with the '#' character
#   - Blank lines are ignored
#   - Groups of hosts are delimited by [header] elements
#   - You can enter hostnames or ip addresses
#   - A hostname/ip can be a member of multiple groups

# Ex 1: Ungrouped hosts, specify before any group headers.

## green.example.com
## blue.example.com
## 192.168.100.1
## 192.168.100.10

# Ex 2: A collection of hosts belonging to the 'webservers' group
[ansible_clients]
# 192.168.1.110 ansible_ssh_user=user ansible_ssh_pass=123
# 192.168.1.110 ansible_ssh_user=vagrant ansible_ssh_pass=vagrant
192.168.1.110 ansible_ssh_user=vagrant
## [webservers]
## alpha.example.org
## beta.example.org
## 192.168.1.100
## 192.168.1.110

# If you have multiple hosts following a pattern you can specify
# them like this:

## www[001:006].example.com

# Ex 3: A collection of database servers in the 'dbservers' group

## [dbservers]
##
## db01.intranet.mydomain.net
## db02.intranet.mydomain.net
## 10.25.1.56
## 10.25.1.57

# Here's another example of host ranges, this time there are no
# leading 0s:

3. create a sample.yml at the user home directory of any folder that you like, and copy the cotent of sample.yml file

What it does it to create a http apache server and set it up, and starts the service uisng and demo of the index.html sample

4. Run the ansible sample project, open a terminal at the sample.yml path and the run it.

linux
ansible-playbook  sample.yml

MAC
ansible-playbook -i ansible/  sample_3.yml

ansible is the folder that we previuos created only for MAC OS 
