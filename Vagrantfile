VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty64"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.hostname = "ninja"
  config.vm.network "private_network", ip: "172.21.12.10"
  
  #VB name
  config.vm.define :ninja do |ninja|
  end

  config.vm.provider "virtualbox" do |vb|
    vb.name = "ninja"
    vb.cpus = 2
    # Use VBoxManage to customize the VM. For example to change memory:
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  config.ssh.forward_agent = true

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "/Users/punchh_vineet/Desktop/pythonVirtual/vagrant-test/", "/home/ubuntu/",
      mount_options: ["noatime,intr,nordirplus,nolock,async,noacl,fsc,tcp"],
      type: "nfs"

  config.vm.boot_timeout = 9000

  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/new.yml"
    ansible.inventory_path = "provisioning/inventory"
    ansible.sudo = true
  end
end