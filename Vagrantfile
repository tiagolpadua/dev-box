# -*- mode: ruby -*-
# vi: set ft=ruby :

# https://stackoverflow.com/questions/47415732/best-way-to-install-docker-on-vagrant

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"

  # require plugin https://github.com/leighmcculloch/vagrant-docker-compose
  # config.vagrant.plugins = "vagrant-docker-compose"

  # install docker and docker-compose
  # config.vm.provision :docker
  # config.vm.provision :docker_compose

  # updates
  # config.vm.provision "shell", inline: "sudo apt update"

  # config.vm.provision "shell", inline: "sudo apt -y upgrade"

  # config.vm.provision "shell", inline: "sudo apt -y install ansible"

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.verbose = true
    ansible.become = true
    ansible.galaxy_role_file = "requirements.yml"
    ansible.galaxy_roles_path = "/etc/ansible/roles"
    ansible.galaxy_command = "sudo ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path} --force"
  end

  # install essential tools
  # config.vm.provision "shell", inline: "sudo apt-get install -y zip unzip"

  # install sdkman
  # config.vm.provision "shell", inline: "curl -s https://get.sdkman.io | bash", privileged: false
  # config.vm.provision "shell", inline: "source $HOME/.sdkman/bin/sdkman-init.sh", privileged: false

  # config.vm.provision "shell", inline: <<-SHELL
  #   sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config    
  #   systemctl restart sshd.service
  # SHELL

  # config.ssh.username = 'vagrant'
  # config.ssh.password = 'vagrant'
  # config.ssh.insert_key = false

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "8192"
    vb.cpus = 2
  end

end