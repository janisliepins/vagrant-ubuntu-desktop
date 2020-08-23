Vagrant.configure("2") do |config|

  config.vagrant.plugins = ["vagrant-disksize", "vagrant-vbguest"]

  config.vm.box = "ubuntu/bionic64"

  config.disksize.size = "75GB"

  config.vbguest.auto_update = true

  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.synced_folder "./workspace", "/home/vagrant/workspace"
  config.vm.synced_folder "./ansible", "/vagrant/ansible"

  config.vm.hostname = "ubuntu-desktop"

  config.vm.network "private_network", ip: "192.168.50.10"

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.name = "ubuntu-desktop"
    vb.memory = 8192
    vb.cpus = 4
    vb.customize ["modifyvm", :id, "--vram", "128"]
    vb.customize ['modifyvm', :id, '--clipboard', 'bidirectional']
    vb.customize ["modifyvm", :id, "--monitorcount", "2"]
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "/vagrant/ansible/playbooks/main.yml"
  end

end
