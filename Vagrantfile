Vagrant.configure("2") do |config|

    # Configurações Globais

    config.vm.box = "centos/7"
    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
    end

    # Configurações da máquina virtual para Wordpress
    config.vm.define "wordpress" do |wp|
        wp.vm.network "private_network", ip: "192.192.10.10"
        wp.vm.synced_folder ".", "/vagrant"
        wp.vm.provision "shell", inline: <<-SHELL
            # yum update -y
            hostnamectl set-hostname ansible-wordpress
            cat /vagrant/key/vagrant-key.pub >> .ssh/authorized_keys
            yum install net-tools mlocate vim -y
        SHELL
    end

    # Configuração de máquina virtual para Ansible   
    config.vm.define "ansible" do |ansible|
        ansible.vm.network "private_network", ip: "192.192.10.11"
        ansible.vm.synced_folder ".", "/vagrant"
        ansible.vm.provision "shell", inline: <<-SHELL
            # yum update -y
            hostnamectl set-hostname ansible-ansible
            cat /vagrant/key/vagrant-key.pub >> .ssh/authorized_keys
            cp /vagrant/key/vagrant-key /home/vagrant
            cp /vagrant/hosts /home/vagrant
            cp /vagrant/provision.yml /home/vagrant
            chmod 600 /home/vagrant/vagrant-key
            chown vagrant:vagrant /home/vagrant/vagrant-key
            # cp /vagrant/* /home/vagrant
            rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
            yum install net-tools mlocate vim ansible python -y 
            yum install epel-release -y
            rpm -Uvh //mirror.webtatic.com/yum/el7/webtatic-release.rpm
            # ansible-playbook -i /vagrant/configs/ansible/hosts /vagrant/configs/ansible/playbook.yaml
        SHELL
    end
end