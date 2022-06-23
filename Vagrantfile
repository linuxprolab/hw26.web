# -*- mode: ruby -*-
# vim: set ft=ruby :
# -*- mode: ruby -*-
# vim: set ft=ruby :

MACHINES = {
  :'webapp' => {
    :host_name => 'webapp',
    :box_name => "centos/8",
    :net => [
      {ip: '192.168.0.1', adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "internal-net"},
    ],
    :ports => [
      {guest: 22, host: 22001, id: 'ssh'}, 
      {guest: 8443, host: 8443}, 
    ],
  },
}

Vagrant.configure("2") do |config|

  MACHINES.each do |boxname, boxconfig|

    config.vm.define boxname do |box|
      box.vm.synced_folder ".", "/vagrant", type: "rsync", disabled: true
      box.vm.box = boxconfig[:box_name]
      box.vm.host_name = boxname.to_s

      if boxconfig.key?(:public)
         box.vm.network "public_network", boxconfig[:public]
      end

      boxconfig[:net].each do |ipconf|
        box.vm.network "private_network", ipconf
      end
      if boxconfig[:ports]
        boxconfig[:ports].each do |portconf|
          box.vm.network "forwarded_port", portconf
        end
      end 
      if boxconfig[:memory]
        box.vm.provider "virtualbox" do |v|
          v.memory = boxconfig[:memory]
       #   v.cpus = box[:cpus]
        end
      end 
     # box.vm.provision "ansible" do |ansible|
     #   ansible.playbook = "provisioning/main.yml"
      #end
    end
  end
end

