VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/xenial"
  config.vm.box_url = "https://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-vagrant.box"

  # Network
  config.vm.network :private_network, ip: "192.168.17.2"
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.hostname = "tomcat"

  # VirtualBox
  config.vm.provider :virtualbox do |vb|
    vb.name = "tomcat"
  end

  # Ansible provisioner
  config.vm.provision "ansible" do |ansible|
    ansible.host_key_checking = false
    ansible.limit = "all"
    ansible.inventory_path = "provisioning/inventory"
    ansible.playbook = "provisioning/playbook.yml"
  end

end