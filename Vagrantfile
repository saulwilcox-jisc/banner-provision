# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
# config.vm.box = "https://github.com/holms/vagrant-centos7-box/releases/download/7.1.1503.001/CentOS-7.1.1503-x86_64-netboot.box"
config.vm.box = "https://github.com/CommanderK5/packer-centos-template/releases/download/0.7.2/vagrant-centos-7.2.box"
  config.vm.network "private_network", ip: "55.55.55.5"

# Built-in folders from Guest Additions
config.vm.synced_folder "~/www-dev/jisc-banner", "/var/www/jisc-banner"

# Note mount options which are important to avoid permissions quirks
#config.vm.synced_folder "~/jisc-banner", "/var/www",
#    owner: "vagrant",
#    group: "www-data",
#    mount_options: ["dmode=775,fmode=664"]

# NFS with useful options
# config.vm.synced_folder "~/www-dev/jisc-banner", "/var/www/jisc-banner", nfs: true, linux__nfs_options:['rw','no_subtree_check','all_squash','async']

  # In some cases Drupal can be slow unless NFS or rsync are used
  # config.vm.synced_folder "~/jisc-banner", "/var/www", type: 'rsync'

  config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
      vb.memory = "1024"
  end


  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "_provision-ansible/manifest.yml"
  end

end
