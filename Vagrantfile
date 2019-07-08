##############################################################################
# Simple Docker deployment location
###############################################################################
Vagrant.configure(2) do |config|

  config.vm.define 'docker' do |nodeconfig|
    nodeconfig.vm.hostname = 'docker'
    nodeconfig.vm.box = 'accanto/xenial'
    nodeconfig.vm.network 'private_network', ip: '192.168.56.110'

    nodeconfig.vm.provider "virtualbox" do |virtualbox|
      virtualbox.name = 'docker'
      virtualbox.gui = false
      virtualbox.cpus = 2
      virtualbox.memory = 4096
      virtualbox.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
      virtualbox.customize [ "modifyvm", :id, "--natnet1", "192.168.222.0/24"]
    end

    nodeconfig.vm.provider :libvirt do |libvirt|
      libvirt.cpus = 2
      libvirt.memory = 4096
      libvirt.nested = true
      libvirt.cpu_mode = 'host-passthrough'
    end

    nodeconfig.vm.provision "ansible_local" do |ansible|
      ansible.become = true
      ansible.playbook = "start-dockerlocation.yml"
    end
  end

end
