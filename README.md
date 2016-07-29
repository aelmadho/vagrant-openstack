# Openstack Simulation Environment 
Provisioning and deployment environment for openstack cloud platform.  This will be utilizing the ansible-openstack project.

### Overview

Utilizing internal host-only network to allow for management inerfaces on the various openstack related services, keeping the NAT IP as the main service IP.  This is being validated and is in work in progress.

![Overview](docs/openstack_vagrant_vbox)

### Requirements:

- VirtualBox 5.1.2
- Vagrant 1.8.5
- [Vagrant LandRush Plugin](https://github.com/vagrant-landrush/landrush)
- Python 2.7
- Pip & virtualenv

### Setup Instructions:

Assuming python and pip environment (virtualenv) is installed, install the required python packages for Ansible by running the following command:

```
pip install -r requirements.txt
```

This will install Ansible, which you can use as part of the Vagrant provisioning process, as well as ad-hoc provisioning, or orchestrated provisioning utilziing the "ansible-playbook" command.  

In order to launch the environment, run the command below to statisfy any vagrant plugin requiremnts:

```
vagrant plugin install landrush
```

### Run it!

Then follow by launching the virtual environment:

```
vagrant up
```
