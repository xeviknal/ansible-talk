# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define :balancer do |balancer|
	  # All Vagrant configuration is done here. The most common configuration
	  # options are documented and commented below. For a complete reference,
	  # please see the online documentation at vagrantup.com.

	  # Every Vagrant virtual environment requires a box to build off of.
	  balancer.vm.box = "debian-8.2.0-amd64_virtualbox.box"

	  # The url from where the 'config.vm.box' box will be fetched if it
	  # doesn't already exist on the user's system.
	  balancer.vm.box_url = "https://s3.eu-central-1.amazonaws.com/ffuenf-vagrantboxes/debian/debian-8.2.0-amd64_virtualbox.box"

	  # Create a forwarded port mapping which allows access to a specific port
	  # within the machine from a port on the host machine. In the example below,
	  # accessing "localhost:8080" will access port 80 on the guest machine.

	  # Create a private network, which allows host-only access to the machine
	  # using a specific IP.
	  balancer.vm.network :private_network, ip: "192.168.56.13"

	  # Provider-specific configuration so you can fine-tune various
	  # backing providers for Vagrant. These expose provider-specific options.
	  # Example for VirtualBox:
	  #
	   balancer.vm.provider :virtualbox do |vb|
	     # Use VBoxManage to customize the VM. For example to change memory:
	     vb.customize ["modifyvm", :id, "--memory", "512"]
	   end
  end
  config.vm.define :frontend do |frontend|
	  # All Vagrant configuration is done here. The most common configuration
	  # options are documented and commented below. For a complete reference,
	  # please see the online documentation at vagrantup.com.

	  # Every Vagrant virtual environment requires a box to build off of.
	  frontend.vm.box = "debian-8.2.0-amd64_virtualbox.box"

	  # The url from where the 'config.vm.box' box will be fetched if it
	  # doesn't already exist on the user's system.
	  frontend.vm.box_url = "https://s3.eu-central-1.amazonaws.com/ffuenf-vagrantboxes/debian/debian-8.2.0-amd64_virtualbox.box"

    frontend.vm.provider :virtualbox do |vb|
     # Use VBoxManage to customize the VM. For example to change memory:
     vb.customize ["modifyvm", :id, "--memory", "512"]
    end
  end
  config.vm.define :database do |db|
	  # All Vagrant configuration is done here. The most common configuration
	  # options are documented and commented below. For a complete reference,
	  # please see the online documentation at vagrantup.com.

	  # Every Vagrant virtual environment requires a box to build off of.
	  db.vm.box = "debian-8.2.0-amd64_virtualbox.box"

	  # The url from where the 'config.vm.box' box will be fetched if it
	  # doesn't already exist on the user's system.
	  db.vm.box_url = "https://s3.eu-central-1.amazonaws.com/ffuenf-vagrantboxes/debian/debian-8.2.0-amd64_virtualbox.box"

	  # mysql
	  db.vm.network :forwarded_port, guest: 3306, host: 3306

	  # memcached
	  db.vm.network :forwarded_port, guest: 11211, host: 11211

	  # redis
	  db.vm.network :forwarded_port, guest: 6379, host: 6379

	  # elasticsearch
	  db.vm.network :forwarded_port, guest: 9200, host: 9200

	  # Create a private network, which allows host-only access to the machine
	  # using a specific IP.
	  db.vm.network :private_network, ip: "192.168.56.12"

    db.vm.provider :virtualbox do |vb|
     # Use VBoxManage to customize the VM. For example to change memory:
     vb.customize ["modifyvm", :id, "--memory", "512"]
    end
  end
end
