Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  config.vm.define "manager" do |manager|
    manager.vm.hostname = "manager"
    manager.vm.network "private_network", ip: "192.168.1.2"
    manager.vm.network "forwarded_port", guest: 80, host: 8090
  end

  config.vm.define "worker1" do |worker1|
    worker1.vm.hostname = "worker1"
    worker1.vm.network "private_network", ip: "192.168.1.3"
  end

  config.vm.define "worker2" do |worker2|
    worker2.vm.hostname = "worker2"
    worker2.vm.network "private_network", ip: "192.168.1.4"
  end

  # Provisionamento com Ansible local
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "/vagrant/ansible/playbook.yml"
    ansible.inventory_path = "/vagrant/ansible/inventory.ini"
  end
end
