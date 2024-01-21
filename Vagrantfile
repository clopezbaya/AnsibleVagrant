Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/bionic64"
    config.vm.network "private_network", ip: "192.168.33.40"
    config.vm.network "forwarded_port", guest: 80, host: 9000
    config.vm.provider "virtualbox" do |vbox|
        vbox.memory = "2048"
        vbox.cpus = "2"
    end
    # Aprovisionamiento con Ansible
    config.vm.provision "shell", inline: <<-SHELL
        sudo apt-add-repository ppa:ansible/ansible -y
	    sudo apt update
	    sudo apt install ansible -y
	    ansible --version
    SHELL
  
    # Lectura desde ansible_local al playbook definido
    config.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "playbook.yml"
    end
  end