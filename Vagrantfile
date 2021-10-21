# -*- mode: ruby -*-
# vi: set ft=ruby :

ANSIBLE_IP      = "172.16.8.5"
MASTER_IP       = "172.16.8.10"
NODE_01_IP      = "172.16.8.11"
NODE_02_IP      = "172.16.8.12"

Vagrant.configure("2") do |config|
  config.vm.box = "geerlingguy/ubuntu2004"
  config.vm.box_version = "1.0.2" # TODO: gseng - 1.0.3

  boxes = [
    { :name => "master",  :ip => MASTER_IP,  :cpus => 1, :memory => 2048 },
    { :name => "node-01", :ip => NODE_01_IP, :cpus => 1, :memory => 2048 },
    { :name => "node-02", :ip => NODE_02_IP, :cpus => 1, :memory => 2048 },
    { :name => "ansible", :ip => ANSIBLE_IP, :cpus => 1, :memory => 512  },
  ]

  boxes.each do |opts|
    config.vm.define opts[:name] do |box|
      box.vm.hostname = opts[:name]
      box.vm.network :private_network, ip: opts[:ip]

      box.vm.provider "virtualbox" do |vb|
        vb.cpus = opts[:cpus]
        vb.memory = opts[:memory]
      end
    end
  end

  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y nginx
  # SHELL
end
