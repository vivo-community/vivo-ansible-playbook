# vivo-ansible-playbook
Install VIVO 1.12.x and its system requirements on a (local/remote/virtual) machine using Ansible. \
The included Ansible playbook 
* first prepares the machine by installing the [System Requirements](https://wiki.lyrasis.org/display/VIVODOC112x/System+Requirements) described in the VIVO wiki 
* and afterwards installs VIVO following the [Installing VIVO](https://wiki.lyrasis.org/display/VIVODOC112x/Installing+VIVO) guide.

### Why Ansible?
Ansible is a DevOps tool for automating tasks like provisioning, configuration management, 
and application deployment. The tasks are provided as infrastructure as code, so they are testable, 
version controlled and can be integrated into a CI pipeline.

A simple use case for using Ansible for installing VIVO would be a set-up with multiple environments like
development, testing, production or for service providers having multiple machines for different clients.
While syncing all machines manually would be quite laborsome, Ansible could save you time by automating it.


### Dependencies
The playbook uses the Ansible roles listed in `provisioning/requirements.yml`.
Each role can be configured within the playbook using the role's defaults and variables below the role name.
To learn about each role's specific variables and defaults, please see their respective GitHub page:
* [robertdebock.core_dependencies](https://github.com/robertdebock/ansible-role-core_dependencies) : prepare machine for ansible
* [robertdebock.java](https://github.com/robertdebock/ansible-role-java) : install java 
* [geerlingguy.solr](https://github.com/geerlingguy/ansible-role-solr) : install solr 
* [robertdebock.tomcat](https://github.com/robertdebock/ansible-role-tomcat) : install tomcat
* [gantsign.maven](https://github.com/gantsign/ansible-role-maven) : install maven
* [vivo_community.vivo](https://github.com/vivo-community/ansible-role-vivo) : install VIVO

Additional hints on how to configure [vivo_community.vivo](https://github.com/vivo-community/ansible-role-vivo) 
can be found in the wiki:
* [How to configure git repositories and branches for VIVO, Vitro, VIVO languages, Vitro languages](https://github.com/vivo-community/vivo-ansible-playbook/wiki/configure-git-repositories-and-branches-for-VIVO,-Vitro,-VIVO-languages,-Vitro-languages)
* [How to overwrite VIVO settings, runtime properties, application setup](https://github.com/vivo-community/vivo-ansible-playbook/wiki/overwrite-VIVO-settings,-runtime-properties,-application-setup)


### Testing
Before executing the playbook on your machine, you can configure the playbook variables
and do a test run using the provided Vagrantfile to provision the playbook to a virtual machine or docker first.
In the wiki are some instructions to get a [test environment on your local machine](https://github.com/vivo-community/vivo-ansible-playbook/wiki/test-setup) going.

### Disclaimer
This Ansible playbook and the accompanying Vagrant setup are intended for development and experimentation only:\
the setup and security of your servers is ultimately YOUR responsibility.