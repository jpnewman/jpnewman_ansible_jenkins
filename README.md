
# Jenkins Stack

This repo contains a vagrant file to create a Jenkins Server, via the following Ansible roles: -

- geerlingguy.firewall
- geerlingguy.security
- geerlingguy.git
- geerlingguy.jenkins
- votum.jenkins
- retr0h.logrotate
- jpnewman.common
- jpnewman.java
- jpnewman.locale-timezone
- jpnewman.nginx

For more information look at the following readmes: -

- ```./Vagrantfiles/MiniStack/README.md```

# Install Vagrant Plugin

~~~bash
vagrant plugin install vagrant-triggers
vagrant plugin install vagrant-cachier
vagrant plugin install vagrant-hostmanager
~~~

# Install Python requirements

~~~bash
sudo pip install -r requirements.txt
~~~

# Install Ansible Roles

~~~bash
ansible-galaxy install -r requirements.yml -p roles
~~~

# Run

### Testing

~~~
ansible-playbook --syntax-check --list-tasks playbook.yml -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory
~~~

## License

MIT / BSD

## Author Information

John Paul Newman
