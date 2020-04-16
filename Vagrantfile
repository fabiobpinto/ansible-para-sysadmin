# -*- mode: ruby -*-
# vi: set ft=ruby  :

machines = {
  "automacao" => {"memory" => "1024", "cpu" => "2", "ip" => "200", "image" => "centos/7"},
  "webserver" => {"memory" => "512", "cpu" => "1", "ip" => "201", "image" => "debian/buster64"},
  "database" => {"memory" => "512", "cpu" => "1", "ip" => "202", "image" => "centos/7"}
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
    end
  end
  config.vm.provision "shell", inline: <<-SHELL 
  echo '192.168.254.200 automacao.sysadmin.domain automacao' >> /etc/hosts
  echo '192.168.254.201 webserver.sysadmin.domain webserver' >> /etc/hosts
  echo '192.168.254.202 database.sysadmin.domain database' >> /etc/hosts
  SHELL
end
