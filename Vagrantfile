# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

# Private cloud machine configuration for base Openstack install
machines = {
  'controller'    => ['172.28.128.2', '8', '2048', false],
  'network'       => ['172.28.128.3', '2', '1024', false], 
  'compute01'     => ['172.28.128.4', '2', '2048', false],
  'compute02'     => ['172.28.128.5', '2', '2048', false]
}

Vagrant.configure (VAGRANTFILE_API_VERSION) do |config|

  config.ssh.insert_key = false

  machines.each do | (name, cfg) |

    ipaddr, cpu, ram, gui = cfg

    config.vm.define name do |machine|
      machine.vm.box = 'ubuntu/trusty64'
      machine.vm.hostname = name
      machine.vm.network "private_network", :type => 'static', :ip => ipaddr, :name => 'vboxnet0', :adapter => 2

      machine.vm.provider 'virtualbox' do |vbox|
        vbox.memory = ram
        vbox.cpus = cpu
        vbox.gui = gui
      end

      machine.vm.provision "shell", :inline => 'cp -f /vagrant/etc/hosts /etc/hosts'
    end

  end
end
