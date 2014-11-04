# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.forward_agent = true
  #config.ssh.private_key_path = "~/Dropbox/Keys/mozilla_vitillo"

  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 8
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.sudo = true
    ansible.verbose = "vv"
    ansible.host_key_checking = false
    ansible.raw_ssh_args = ['-o UserKnownHostsFile=/dev/null']
    ansible.extra_vars = { ansible_ssh_user: 'vagrant',
                           ansible_connection: 'ssh',
                           ansible_ssh_args: '-o ForwardAgent=yes'}
  end

end
