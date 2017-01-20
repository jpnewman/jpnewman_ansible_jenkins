
# Jenkins MiniStack

The vagrant file it this directory create a mini test stack with the following: -

- Jenkins Server

# Requirements

The following Vagrant plugins can be used:

 - [vagrant-cachier](https://github.com/fgrehm/vagrant-cachier)
 - [vagrant-hostmanager](https://github.com/devopsgroup-io/vagrant-hostmanager)

# Versions

- Vagrant 1.8.1
  - vagrant-berkshelf (4.1.0)
  - vagrant-cachier (1.2.1)
  - vagrant-hostmanager (1.8.1)
  - vagrant-omnibus (1.4.1)
  - vagrant-proxyconf (1.5.2)
  - vagrant-share (1.1.5, system)
  - vagrant-triggers (0.5.2)
  - vai (0.9.3)

# Create self-signed unsecured cert

~~~
openssl req -x509 -batch -nodes -newkey rsa:2048 -keyout ../../files/certs/notsecure.key -out ../../files/certs/notsecure.crt -config ../../files/certs/notsecure.cnf -days 1825
~~~

> Check cert

~~~
openssl x509 -in ../../files/certs/notsecure.crt -text
~~~

# Run

### Vagrant

~~~
vagrant up
~~~

### Specific tags

~~~
ANSIBLE_HOST_KEY_CHECKING=false ansible-playbook playbook.yml -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory --tags "jenkins-server"
~~~

### Testing

~~~
ansible-playbook --syntax-check --list-tasks playbook.yml -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory
~~~

## Server URL

<https://jenkins-server/>

# Boxes

|Box|Description|Vagrant Name|Ansible Host|
|---|---|---|---|---|
|```10.10.10.20```|Jenkins Server|```jenkins```|```jenkins-server```|

# Ports

|Server|Application|Type|Port|
|---|---|---|---|
|```10.10.10.20```|jenkins|TCP|```80```|
|```10.10.10.20```|jenkins|TCP|```443```|
