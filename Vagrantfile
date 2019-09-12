Vagrant.configure("2") do |config|

    config.vm.box = "ubuntu/xenial64"
    config.vm.box_version = "20180917.0.0"
    config.vm.box_download_insecure = true

    config.vm.provider "virtualbox" do |vb|
        vb.name = "kuro-oujisama"

        vb.memory = 3072
        vb.cpus = 2

        vb.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
    end

    config.vm.network "private_network", ip: "192.168.10.80"
    config.vm.network "forwarded_port", guest: 22, host: 2902

    config.vm.synced_folder "./code", "/home/vagrant/code"

    config.vm.provision :docker_compose, yml: "/home/vagrant/code/docker-compose.yml", run: "always"
end