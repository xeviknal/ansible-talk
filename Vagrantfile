# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define :balancer do |balancer|
	  balancer.vm.box = "debian-8.2.0-amd64_virtualbox.box"
	  balancer.vm.box_url = "https://s3.eu-central-1.amazonaws.com/ffuenf-vagrantboxes/debian/debian-8.2.0-amd64_virtualbox.box"
	  balancer.vm.network :private_network, ip: "192.168.56.13"

	   balancer.vm.provider :virtualbox do |vb|
	     # Use VBoxManage to customize the VM. For example to change memory:
	     vb.customize ["modifyvm", :id, "--memory", "512"]
	   end
  end
  config.vm.define :frontend do |frontend|
	  frontend.vm.box = "debian-8.2.0-amd64_virtualbox.box"
	  frontend.vm.box_url = "https://s3.eu-central-1.amazonaws.com/ffuenf-vagrantboxes/debian/debian-8.2.0-amd64_virtualbox.box"
	  frontend.vm.network :private_network, ip: "192.168.56.14"

    frontend.vm.provider :virtualbox do |vb|
     # Use VBoxManage to customize the VM. For example to change memory:
     vb.customize ["modifyvm", :id, "--memory", "512"]
    end
  end
  config.vm.define :database do |db|
	  # Every Vagrant virtual environment requires a box to build off of.
	  db.vm.box = "debian-8.2.0-amd64_virtualbox.box"
	  db.vm.box_url = "https://s3.eu-central-1.amazonaws.com/ffuenf-vagrantboxes/debian/debian-8.2.0-amd64_virtualbox.box"

	  # mysql
	  db.vm.network :forwarded_port, guest: 3306, host: 3306

	  # memcached
	  db.vm.network :forwarded_port, guest: 11211, host: 11211

	  # redis
	  db.vm.network :forwarded_port, guest: 6379, host: 6379

	  # elasticsearch
	  db.vm.network :forwarded_port, guest: 9200, host: 9200

	  db.vm.network :private_network, ip: "192.168.56.15"

    db.vm.provider :virtualbox do |vb|
     # Use VBoxManage to customize the VM. For example to change memory:
     vb.customize ["modifyvm", :id, "--memory", "512"]
    end
  end
end
