# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "ubuntu/trusty64"
  config.vm.network :forwarded_port, guest: 80, host: 8080 

  config.vm.provider :virtualbox do |v|
    v.memory = 4096
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/getreqs.yml"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/deploy.yml"
    ansible.groups = {
      "master" => ["default"],
      "slaves" => ["default"]
    }
  end

end
