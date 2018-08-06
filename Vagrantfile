# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.provision "shell", inline: "apt -y install python"

  config.vm.define "jenkins" do |jenkins|
      jenkins.vm.box = "ubuntu/xenial64"
      jenkins.vm.network "private_network", ip: "192.168.50.12"
      jenkins.vm.network "forwarded_port", guest: 8080, host: 8080
      jenkins.vm.provision "ansible" do |ansible|
        ansible.galaxy_role_file = "requirements.yml"
        ansible.playbook = "jenkins.yml"
        ansible.galaxy_roles_path = "roles/"
      end
  end

  config.vm.define "staging" do |staging|
      staging.vm.box = "ubuntu/xenial64"
      staging.vm.network "private_network", ip: "192.168.50.13"
      staging.vm.network "forwarded_port", guest: 8080, host: 8081
      staging.vm.provision "ansible" do |ansible|
        ansible.playbook = "setup-staging.yml"
      end
  end

  config.vm.define "prod" do |prod|
      prod.vm.box = "ubuntu/xenial64"
      prod.vm.network "private_network", ip: "192.168.50.14"
      prod.vm.network "forwarded_port", guest: 8080, host: 8082
      prod.vm.provision "ansible" do |ansible|
        ansible.playbook = "setup-prod.yml"
      end
  end


end
