# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'
current_dir = File.dirname(File.expand_path(__FILE__))
yamlfile    = YAML.load_file("#{current_dir}/vagrant.yml")
config      = yamlfile

hostname = config['config']['vm']['hostname']
token = config['provider']['token']
image = config['provider']['image'] 
region = config['provider']['region']
size = config['provider']['size']

Vagrant.configure(2) do |config|

  config.vm.box = "digital_ocean"
  config.vm.hostname = hostname
  config.ssh.username = 'vagrant'
  config.vm.synced_folder ".", "/vagrant", type: "rsync",
    rsync__exclude: [".git/"]

  config.vm.provider :digital_ocean do |provider, override|
    override.ssh.private_key_path = '~/.ssh/id_rsa'
    override.vm.box = 'digital_ocean'
    override.vm.box_url = "https://github.com/devopsgroup-io/vagrant-digitalocean/raw/master/box/digital_ocean.box"
    provider.token = token
    provider.image = image
    provider.region = region
    provider.size = size
  end

  config.vm.provision :ansible do |ansible|
    ansible.ask_vault_pass = true
    ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
    ansible.verbose = false #"vvv"
    ansible.playbook = "provisioning/main.yml"
  end

end
