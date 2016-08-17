# Vagrant/Ansible FreeSWITCH


## Digital Ocean API Key

Go to https://cloud.digitalocean.com/settings/api/tokens to create a Read/Write API key.


## Dynamic DNS API Key

Get a dynamic dns API key from your DNS provider. (Tested with Hurricane Electric)


## Install Software

If you don't already have vagrant and ansible installed, do that.


## Install Role Dependencies

`ansible-galaxy install -r provisioning/install_roles.yml`


## Override Ansible variables

If you don't you aren't going to have a functional freeswitch. More on this soon.


## Start VPS

`vagrant up --provider=digital_ocean`


## Additional Resources
* https://github.com/devopsgroup-io/vagrant-digitalocean
* https://www.vagrantup.com/docs/


