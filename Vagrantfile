Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"
  config.vm.network "private_network", ip: "192.168.56.10"
  config.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
  config.vm.usable_port_range = 8080..8090
  config.vm.synced_folder "./data", "/var/www/html"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 1024
    vb.cpus = 2
  end
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get upgrade
    apt-get install -y apache2
  SHELL
end
