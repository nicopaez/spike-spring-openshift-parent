# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.network "forwarded_port", guest: 8080, host: 8090

  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
  #   vb.gui = true
    vb.memory = "1024"
  end

  config.vm.provision "shell", inline: <<-SHELL
    echo "I am provisioning..."
    # java and maven
    sudo add-apt-repository ppa:openjdk-r/ppa
    sudo apt-get update
    sudo apt-get install -y openjdk-8-jdk
    sudo apt-get install -y maven
    
    # docker
    sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
    sudo echo "deb https://apt.dockerproject.org/repo ubuntu-trusty main" > /etc/apt/sources.list.d/docker.list
    sudo apt-get update
    sudo apt-get purge lxc-docker
    sudo apt-get install -y linux-image-extra-$(uname -r)
    sudo apt-get install -y docker-engine
    sudo service docker start
    sudo usermod -aG docker vagrant
    docker pull openjdk:8-jre-alpine

    # openshift tools
    wget https://github.com/openshift/origin/releases/download/v1.5.1/openshift-origin-client-tools-v1.5.1-7b451fc-linux-64bit.tar.gz
    tar -xvf openshift-origin-client-tools-v1.5.1-7b451fc-linux-64bit.tar.gz
    mv openshift-origin-client-tools-v1.5.1-7b451fc-linux-64bit oc-tool
    ln -s /home/vagrant/oc-tool/oc /bin/oc
        
    date > /etc/vagrant_provisioned_at
  SHELL
end
