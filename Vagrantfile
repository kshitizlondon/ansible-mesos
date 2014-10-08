Vagrant.configure("2") do |config|
    config.vm.box = "hashicorp/precise64"
    config.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--memory", "1024"]
        vb.customize ["modifyvm", :id, "--cpus", "2"]
    end

    master_ip = "192.168.50.30"
    config.vm.define :master do |c|
      c.vm.hostname = "master"
      c.vm.network :private_network, ip: master_ip
    end

    slave1_ip = "192.168.50.31"
    config.vm.define :slave do |c|
      c.vm.hostname = "slave"
      c.vm.network :private_network, ip: slave1_ip
    end

    slave2_ip = "192.168.50.32"
    config.vm.define :slave2 do |c|
      c.vm.hostname = "slave2"
      c.vm.network :private_network, ip: slave2_ip
    end

    slave3_ip = "192.168.50.33"
    config.vm.define :slave3 do |c|
      c.vm.hostname = "slave3"
      c.vm.network :private_network, ip: slave3_ip

      c.vm.provision :ansible do |ansible|
        ansible.playbook = "mesos.yml"
        ansible.inventory_path = "./inventory/vagrant"
        ansible.limit = 'all,localhost'
        ansible.extra_vars = {
          app_user: "vagrant",
          app_bot_name: `whoami | xargs echo -n`
        }
        #ansible.verbose = "vvvv"
      end
    end
end
