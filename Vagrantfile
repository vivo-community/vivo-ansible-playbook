# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile to provision VIVO using Ansible

# The primary function of the Vagrantfile is to describe the type of machine required for a project,
# and how to configure and provision these machines.
# The settings within config.vm modify the configuration of the machine that Vagrant manages.
# For a complete reference, please see the online documentation at https://docs.vagrantup.com.

Vagrant.configure("2") do |config|
  # Every Vagrant development environment requires a box (=pre-configured virtual machine).
  # You can find a searchable list of available boxes at https://vagrantcloud.com/search.
  config.vm.box = "bento/debian-10"
  
  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine.
  # NOTE: This will enable public access to the opened port
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "forwarded_port", guest: 8983, host: 8983
  
  # Share this repo incl. the Ansible playbook to the guest VM.
  config.vm.synced_folder ".", "/vagrant"

  # Provider-specific configuration for virtualbox.
  config.vm.provider "virtualbox" do |vb|
    vb.name = "vivo_box"
    # Display the VirtualBox GUI when booting the machine
    vb.gui = false
    # Customize the number of CPUs on the VM:
    vb.cpus = 1
    # Customize the amount of memory on the VM:
    vb.memory = "4096"
  end

  # Run Ansible from the Vagrant VM
  config.vm.provision "ansible_local" do |ansible|
    # configure Python3 and Ansible on VM
    ansible.install = true
    ansible.install_mode = "pip_args_only"
    ansible.pip_install_cmd = "sudo apt install -y python3-distutils && curl https://bootstrap.pypa.io/get-pip.py | sudo python3"
    ansible.pip_args = "ansible==2.10.7"
    ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3" }

    ansible.compatibility_mode = "2.0"
    # locate Ansible playbook to run
    ansible.playbook = "provisioning/playbook.yml"
    # locate file listing required roles that are used in playbook
    ansible.galaxy_role_file = "provisioning/requirements.yml"
  end
end
