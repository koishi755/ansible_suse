$install_package = <<SCRIPT
sudo zypper update -y
sudo zypper upgrade -y
sudo systemctl stop packagekit
sudo zypper install -y sshpass
sudo pip3 install --upgrade pip
sudo pip3 install ansible
SCRIPT

Vagrant.configure("2") do |config|
  
  config.vm.define 'main' do |main|
    main.vm.box = 'sapinstalledsuse'
    main.vm.synced_folder ".", "/opt" #, disabled: true
    main.vm.provision 'shell', inline: $install_package

    main.vm.provider :libvirt do |domain|
      domain.memory = 8000
      domain.cpus = 4
    end
  end
end
