# vivo-ansible-vagrant
Provision VIVO 1.12.x to a virtual machine using Ansible and Vagrant. \
The included Ansible playbook 
* first prepares the VM by installing the [System Requirements](https://wiki.lyrasis.org/display/VIVODOC112x/System+Requirements) described in the VIVO wiki 
* and afterwards installs VIVO following the [Installing VIVO](https://wiki.lyrasis.org/display/VIVODOC112x/Installing+VIVO) guide.

While currently the virtual machine is based on Debian 10, other OS may work as well, since Ansible is multi-platform. If you tried another OS, let us know, and we will include it in this README.

### Prerequisites
* [Git](https://git-scm.com/downloads)
* [Vagrant](https://www.vagrantup.com/downloads.html)
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

Perform the following steps in the terminal (Linux / macOS) or GitBash (Windows).
```
git clone https://github.com/vivo-community/vivo-ansible-vagrant.git
cd vivo-ansible-vagrant
vagrant up
```

When the installation is complete (a few minutes, depending on the download speed), VIVO & Solr can be opened in the browser:
* VIVO : http://localhost:8080/vivo/
* Solr : http://localhost:8983


### Useful Vagrant commands
- `vagrant up`                  -- starts vagrant environment (provisions only on the first vagrant up)
- `vagrant ssh`                 -- connects to machine via SSH
- `vagrant provision`           -- forces re-provisioning of the vagrant machine
- `vagrant reload`              -- restarts vagrant machine, loads new Vagrantfile configuration
- `vagrant reload --provision`  -- restart the virtual machine and force provisioning
- `vagrant halt`                -- stops the vagrant machine
- `vagrant destroy`             -- stops and deletes all traces of the vagrant machine

### Disclaimer
This Vagrant setup and the accompanying Ansible playbook are intended for development and experimentation only.
