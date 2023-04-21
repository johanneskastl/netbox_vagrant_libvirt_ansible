Vagrant.configure("2") do |config|

  ###################################################################################
  config.vm.define "netbox" do |node|

    # which image to use
    node.vm.box = "generic/fedora37"

    # sizing of the VMs
    node.vm.provider "libvirt" do |lv|
      lv.random_hostname = false
      lv.memory = 4096
      lv.cpus = 4
    end

    # set the hostname
    node.vm.hostname = "netbox"

    # disable shared folders
    node.vm.synced_folder ".", "/vagrant", disabled: true
    node.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook-all_nodes.yml"
    end # node.vm.provision

  end # config.vm.define

end # Vagrant.configure
