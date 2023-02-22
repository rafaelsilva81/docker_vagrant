Vagrant.configure("2") do |config|

  config.vm.define "master" do |master|
    master.vm.box = "ubuntu/focal64"
    master.vm.network "private_network", ip: "192.168.50.10"
    master.vm.hostname = "master"
    master.vm.provision "shell", inline: <<-SHELL
      curl -fsSL https://get.docker.com -o get-docker.sh
      sudo sh get-docker.sh
      sudo usermod -aG docker vagrant
    SHELL
  end

  (1..3).each do |i|
    config.vm.define "node0#{i}" do |node|
      node.vm.box = "ubuntu/focal64"
      node.vm.network "private_network", ip: "192.168.50.1#{i}"
      node.vm.hostname = "node0#{i}"
      node.vm.provision "shell", inline: <<-SHELL
        curl -fsSL https://get.docker.com -o get-docker.sh
        sudo sh get-docker.sh
        sudo usermod -aG docker vagrant
      SHELL
    end
  end

end
