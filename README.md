# ansible_openstack_instance
Simple Ansible playbook to create new instance on an OpenStack cloud
Uses os_server module from Ansible 2

Ansible installation and setup on Centos7 virtual instance brought up from kvm image on OpenStack

#install packages
easy_install pip
pip install jinja2
pip install six --upgrade
yum install gcc gcc-devel libffi-devel python-devel openssl-devel libxml-devel libxslt-devel
pip install shade
#install ansible from git
yum install git
git clone git://github.com/ansible/ansible.git --recursive
#set ansible environment to run - every time when logging in
cd ansible/
source hacking/env-setup
#setup ssh keys - for localhost
ssh-keygen -t rsa
cat ~/.ssh/id_rsa.pub  >>  ~/.ssh/authorized_keys"
#add lines to prevenet ssh prompting cofirmation of the key
mkdir /etc/ansible
vi /etc/ansible/ansible.cfg
[defaults]
host_key_checking = False
#create inventory file and add hosts
vi /etc/ansible/hosts
#example for local host
[local_host]
127.0.0.1
#run check for ansible
ansible local_host -m ping
