Vagrant.configure("2") do |config|
  config.vm.define "mariadb" do |node|
    node.vm.network "private_network", ip: "192.168.122.2", lxc__bridge_name: 'virbr0'
    node.vm.box= "debian/stretch64"
    node.vm.provider :lxc do |lxc|
      lxc.container_name = :machine # Sets the container name to 'db'
      lxc.container_name = 'mariadb'  # Sets the container name to 'mysql'
    end
  end
  config.vm.define "wordpress" do |node2|
    node2.vm.network "private_network", ip: "192.168.122.3", lxc__bridge_name: 'virbr0'
    node2.vm.box= "debian/stretch64"
    node2.vm.provider :lxc do |lxc|
      lxc.container_name = :machine # Sets the container name to 'db'
      lxc.container_name = 'wordpress'  # Sets the container name to 'mysql'
    end
  end
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "./ansible/site.yaml"
  end
end
