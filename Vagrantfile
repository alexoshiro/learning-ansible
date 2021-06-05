Vagrant.configure("2") do |config|
    
    config.vm.provider "virtualbox" do |vb|
        vb.memory = 1024
        vb.cpus = 1
    end

    config.vm.define "wordpress" do |wordpress|
        wordpress.vm.box = "ubuntu/trusty64"
        wordpress.vm.network "public_network", ip: "192.168.15.99"
        wordpress.vm.provision "shell",
            inline: "cat /vagrant/configs/id_bionic.pub >> .ssh/authorized_keys"
    end

    config.vm.define "ansible" do |ansible|
        ansible.vm.box = "ubuntu/bionic64"
        ansible.vm.network "public_network", ip: "192.168.15.96"
        ansible.vm.provision "shell",
            inline: "cp /vagrant/id_bionic /home/vagrant && \
                    chmod 600 /home/vagrant/id_bionic && \
                    chown vagrant:vagrant /home/vagrant/id_bionic"
        ansible.vm.provision "shell",
            inline: "apt-get update && \
                     apt-get install -y software-properties-common && \
                     apt-add-repository --yes --update ppa:ansible/ansible && \
                     apt-get install -y ansible"
    end
end