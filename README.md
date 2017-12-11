# loadbalancertask
using vagrant creating a haproxy lb for nginx servers

## Prerequisites on Ubuntu: 

#### Install Ruby (>= 2.2) 
`sudo apt-get install ruby`

#### Install Vagrant

Download: 
`wget https://releases.hashicorp.com/vagrant/2.0.1/vagrant_2.0.1_x86_64.deb`

Install: 
`dpkg -i vagrant_2.0.1_x86_64.deb`

#### Install Ansible:
```
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible
```

### How to run:
Clone the repo to your machine `git clone https://github.com/sandjaie/loadbalancertask.git` and run `vagrant up`
Which will create three VMs namely webserver01, webserver02 and haproxy01

Then run ansible playbook for webserver and haproxy

```ansible-playbook -i inventory/domain.local playbooks/install_nginx.yml```

```ansible-playbook -i inventory/domain.local playbooks/install_haproxy.yml```

 - webserver01 and 02 will run nginx
 - haproxy01 will run haproxy
 
