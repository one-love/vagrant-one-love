# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.define "target" do |target|
        target.vm.box = "debian-jessie"
        target.vm.box_url = "ftp://ftp.lugons.org/vagrant/debian-8.0-x86_64.box"
        target.vm.network :private_network, ip: "192.168.33.34"
    end

    config.vm.define "onelove" do |onelove|
        onelove.vm.box = "debian-jessie"
        onelove.vm.box_url = "ftp://ftp.lugons.org/vagrant/debian-8.0-x86_64.box"
        onelove.vm.network :private_network, ip: "192.168.33.33"
        onelove.vm.provision :ansible, run: "always" do |ansible|
            ansible.playbook = "provision/site.yml"
            ansible.host_key_checking = false
            ansible.groups = {
                "vagrant" => ["onelove"],
            }
        end
    end
end
