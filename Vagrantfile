# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

# Private cloud machine configuration for base Openstack install
machines = {
  'controller.vm'    => ['172.28.128.2', '2', '512', false],
  'network.vm'       => ['172.28.128.3', '2', '512', false], 
  'compute01.vm'     => ['172.28.128.4', '2', '512', false],
  'compute02.vm'     => ['172.28.128.5', '2', '512', false]
}

Vagrant.configure (VAGRANTFILE_API_VERSION) do |config|

  # DNS 
  config.landrush.enabled = true
  config.landrush.tld = "vm"

  # Disable from re-generating SSH keys on every run of "vagrant up"
  config.ssh.insert_key = false

  machines.each do | (name, cfg) |

    ip, cpu, ram, gui = cfg

    config.vm.define name do |machine|
      machine.vm.box = 'ubuntu/trusty64'
      machine.vm.hostname = name
      machine.vm.network "private_network", :ip => ip

      # Ansible Provisioner
      machine.vm.provision "ansible" do |ansible|
        ansible.verbose = ""
        ansible.playbook = "site.yml"
      end

      # Set VM resources
      machine.vm.provider 'virtualbox' do |vbox|
        vbox.memory = ram
        vbox.cpus = cpu
        vbox.gui = gui
      end

    end

  end
end
