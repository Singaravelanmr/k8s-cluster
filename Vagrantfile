
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.define "master" do | w |
  w.vm.hostname = "master"
  w.vm.network "private_network", ip: "192.168.212.13"
  w.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = 2
    vb.name = "master"
  end
  w.vm.provision "setup-hosts", :type => "shell", :path => "k8s-setup-master.sh" do |s|
  end
  w.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y git wget vim curl
   SHELL
  end

  config.vm.box = "ubuntu/bionic64"
  config.vm.define "worker-1" do | w |
      w.vm.hostname = "worker-1"
      w.vm.network "private_network", ip: "192.168.212.14"

      w.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.cpus = 1
        vb.name = "worker-1"
      end
      w.vm.provision "setup-hosts", :type => "shell", :path => "k8s-setup-master.sh" do |s|
    end
   w.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get install -y git wget vim 
   SHELL
  end
end
