Vagrant.configure("2") do |config|
  # Operating system/box
  config.vm.box = "centos/7"
  config.vm.box_version = "1811.02"
  # config.vm.box = "ubuntu/trusty64"
  # config.vm.box_version = "20181203.0.1"

  # Network settings
  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  config.vm.network "public_network", ip: "192.168.0.30"

  # Folder setting
  # NFS requires a host-only network to be created.
  # config.vm.synced_folder ".", "/vagrant", :nfs => { :mount_options => ["dmode=777", "fmode=666"] }
  # config.vm.synced_folder ".", "/var/www/html"

  # Provider setting
  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "1024"
    vb.cpus = 2
  end

  # Provisioning
  # config.vm.provision "shell", path: "install.sh"
  # Run Ansible from the Vagrant Host
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.inventory_path = "provisioning/hosts"
    ansible.limit = "all"
    ansible.verbose = "-vvv"
  end

end
