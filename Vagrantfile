# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  # vagrant box install https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box --name=trusty
  config.vm.box = "trusty"

  #config.vm.define "app2" do |machine|
    #machine.ssh.port = 22
    #machine.vm.network "private_network", ip: "192.168.33.12"
  #end

  config.vm.define "app1" do |machine|

    machine.vm.network "private_network", ip: "192.168.33.11"

    machine.vm.provision "ansible" do |ansible|
      ansible.playbook = "bootstrap.yml"
      ansible.limit = 'all'
      ansible.sudo = true

      #ansible.verbose = "vvvv"
      ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
      ansible.groups = {
        "app" => ["app1", "app2"]
      }
    end
  end
end
