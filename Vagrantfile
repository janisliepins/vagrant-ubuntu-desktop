Vagrant.configure("2") do |config|
  config.vagrant.plugins = ["vagrant-disksize", "vagrant-vbguest"]

  config.vm.box = "ubuntu/bionic64"
  # Optional - enlarge disk (will also convert the format from VMDK to VDI):
  config.disksize.size = "50GB"

  config.vbguest.auto_update = true

  # config.vm.synced_folder ".", "/vagrant", disabled: true
  # config.vm.synced_folder "shared-data/", "/home/ubuntu/shared-data", owner: "root", group: "root"

  config.vm.hostname = "ubuntu-desktop"

  config.vm.network "private_network", ip: "192.168.50.10"

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = true
    vb.name = "ubuntu-desktop"
    vb.memory = 4096
    vb.cpus = 2
    vb.customize ["modifyvm", :id, "--vram", "128"]
    vb.customize ['modifyvm', :id, '--clipboard', 'bidirectional']
    vb.customize ["modifyvm", :id, "--monitorcount", "2"]
  end

  # config.vm.provision "shell", inline: <<-SCRIPT
  #   sudo apt update -y
  # SCRIPT


  # config.vm.provision "shell", path: "install-scripts/desktop.sh"
  # config.vm.provision "shell", path: "install-scripts/chrome.sh"
  # config.vm.provision "shell", path: "install-scripts/vscode.sh"
  # config.vm.provision "shell", path: "install-scripts/docker.sh"
  # config.vm.provision "shell", path: "install-scripts/ansible.sh"



  # Install Docker
  # config.vm.provision :docker

  # Install Docker Compose
  # First, install required plugin https://github.com/leighmcculloch/vagrant-docker-compose:
  # vagrant plugin install vagrant-docker-compose
  # config.vm.provision :docker_compose

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "ansible/main.yml"
  end

  # config.vm.provision "shell", path: "install-docker.sh"
  # config.vm.provision "shell", path: "install-ide.sh"
  # config.vm.provision "shell", path: "install-java-eclipse.sh"

  # config.vm.provision "shell", path: "install-node.sh"
  # config.vm.provision "shell", path: "install-apache-php.sh"

  # config.vm.provision "file", source: "etc_mongod.conf.no-auth", destination: "/tmp/mongod.conf.no-auth"
  # config.vm.provision "file", source: "etc_mongod.conf.auth",    destination: "/tmp/mongod.conf.auth"
  # config.vm.provision "shell", path: "install-mongodb.sh"

  # config.vm.provision "shell", path: "install-mysql.sh"
  # config.vm.provision "shell", path: "install-memcached.sh"

  # config.vm.provision "shell", path: "install-awscli.sh"
end
