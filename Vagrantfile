Vagrant.configure("2") do |config|
  config.vm.provision "shell", path: "script.sh"

  config.vm.define "controle" do |controle|
    controle.vm.box = "shekeriev/debian-11"
    controle.vm.hostname = "controle" #nome que ficará na VM
    controle.vm.network "private_network", ip: "172.17.177.100" #rede em modo host only para comunicação entre as VMs no virtualbox
    controle.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 2
      vb.name = "controle" #nome que ficará no virtualbox
    end
    controle.vm.provision "ansible_local" do |al|
      al.playbook = "playbook.yml"
      al.install_mode = "pip"
    end
  end

  config.vm.define "web" do |web|
    web.vm.box = "shekeriev/debian-11"
    web.vm.hostname = "web" #nome que ficará na VM
    web.vm.network "private_network", ip: "172.17.177.101" #rede em modo host only para comunicação entre as VMs no virtualbox
    web.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 2
      vb.name = "web" #nome que ficará no virtualbox
    end
  end

  config.vm.define "db" do |db|
    db.vm.box = "shekeriev/debian-11"
    db.vm.hostname = "db"
    db.vm.network "private_network", ip: "172.17.177.102" #rede em modo host only para comunicação entre as VMs no virtualbox
    db.vm.provider "vitualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 2
      vb.name = "db"
    end
  end
end

