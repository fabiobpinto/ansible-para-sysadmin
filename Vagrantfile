# -*- mode: ruby -*-
# vi: set ft=ruby  :

machines = {
  "automacao" => {"memory" => "1024", "cpu" => "2", "ip" => "200", "image" => "centos/7"},
  "webserver" => {"memory" => "512", "cpu" => "1", "ip" => "201", "image" => "geerlingguy/debian10"},
  "database" => {"memory" => "512", "cpu" => "1", "ip" => "202", "image" => "bento/centos-8.2"},
  "monitoracao" => {"memory" => "512", "cpu" => "1", "ip" => "203", "image" => "bento/centos-8.2"}
}

Vagrant.configure("2") do |config|

  config.vm.box_check_update = false
  machines.each do |name, conf|
    config.vm.define "#{name}" do |machine|
      machine.vm.box = "#{conf["image"]}"
      machine.vm.hostname = "#{name}.sysadmin.domain"
      machine.vm.network "private_network", ip: "192.168.254.#{conf["ip"]}"
      machine.vm.provider "virtualbox" do |vb|
        vb.name = "#{name}"
        vb.memory = conf["memory"]
        vb.cpus = conf["cpu"]
      end
      if "#{conf["image"]}" == "geerlingguy/debian10"
        machine.vm.provision "shell", inline: "apt update && apt upgrade -y"
        machine.vm.provision "shell", inline: "apt install python -y"
        machine.vm.provision "shell", inline: "apt install vim -y"
      end
      if "#{conf["image"]}" == "centos/7"
        machine.vm.provision "shell", inline: "yum update && yum upgrade -y"
        machine.vm.provision "shell", inline: "yum install epel-release -y"
        machine.vm.provision "shell", inline: "yum install vim -y"
      end
      if "#{conf["image"]}" == "bento/centos-8.2"
        machine.vm.provision "shell", inline: "yum update && yum upgrade -y"
        machine.vm.provision "shell", inline: "yum install epel-release -y"
        machine.vm.provision "shell", inline: "yum install vim -y"
      end
    end
  end
  config.vm.provision "shell", inline: <<-SHELL 
  echo '192.168.254.200 automacao.sysadmin.domain automacao' >> /etc/hosts
  echo '192.168.254.201 webserver.sysadmin.domain webserver' >> /etc/hosts
  echo '192.168.254.202 database.sysadmin.domain database' >> /etc/hosts
  echo '192.168.254.203 monitoracao.sysadmin.domain monitoracao' >> /etc/hosts
  SHELL


end
