# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'
Vagrant.configure("2") do |config|
   config.vm.define "kernel-update" do |kernelupdate|
      kernelupdate.vm.box = "bento/ubuntu-24.04"
      kernelupdate.vm.host_name = "kernel-update"
      kernelupdate.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.cpus = "2"
      end

      kernelupdate.vm.provision "shell", inline: <<-SHELL
        apt-get update
        wget https://kernel.ubuntu.com/mainline/v6.12/amd64/linux-headers-6.12.0-061200_6.12.0-061200.202411220723_all.deb
        wget https://kernel.ubuntu.com/mainline/v6.12/amd64/linux-image-unsigned-6.12.0-061200-generic_6.12.0-061200.202411220723_amd64.deb
        wget https://kernel.ubuntu.com/mainline/v6.12/amd64/linux-modules-6.12.0-061200-generic_6.12.0-061200.202411220723_amd64.deb

        dpkg -i linux-headers* linux-image* linux-modules*
        update-grub
    
        reboot
      SHELL
   end
end
