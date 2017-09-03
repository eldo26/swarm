Vagrant.configure("2") do |config|
  config.vm.box = "centos-7-docker"
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.landrush.host_interface = 'enp0s8'
  config.vm.provision "ansible" do |ansible|
  # ansible.inventory_path = "inventory"
  ansible.playbook = "site.yaml"
  end

  
    config.vm.define "manager-node.com" do |x|
      x.vm.hostname = "manager-node.com"
      x.vm.network "private_network", ip: "172.28.128.10", auto_config: true
    end


  (1..3).each do |count|
    config.vm.define "DC-A-#{count}.com" do |x|
      x.vm.hostname = "DC-A-#{count}.com"
      x.vm.network "private_network", ip: "172.28.128.5#{count}", auto_config: true
    end
  end

  (1..3).each do |count|
    config.vm.define "DC-B-#{count}.com" do |x|
      x.vm.hostname = "DC-B-#{count}.com"
      x.vm.network "private_network", ip: "172.28.128.6#{count}", auto_config: true
    end
  end


end