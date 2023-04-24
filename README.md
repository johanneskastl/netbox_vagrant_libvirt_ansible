# netbox_vagrant_libvirt_ansible

This Vagrant setup creates a VM and configures [Netbox](https://netbox.dev/).

Default OS is Fedora 37. Although that can be changed in the Vagrantfile, please
beware that this will break the Ansible provisioning.

## Vagrant

1. You need vagrant obviously. And ansible. And git...
1. Fetch the box, per default this is `generic/fedora37`, using `vagrant box add
   generic/fedora37`.
1. Make sure the git submodules are fully working by issuing `git submodule init
   && git submodule update`
   `ansible-playbook ansible/playbook-localhost-selfsigned_demo_ca.yml`
1. Run `vagrant up`
1. Find out the VM's IP (e.g. `vagrant address netbox`, if you have vagrant
   address installed) and connect to IP:8080.
1. Log in as `admin` user (password: `admin`).
1. Party!

## Disabling the Ansible provisioning

In case you do not want Ansible to install teleport (because you want to install
it yourself), just comment out the following lines in the `Vagrantfile`:

```hcl
    node.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook-all_nodes.yml"
    end # node.vm.provision
```

You also find all of the playbooks in the `ansible` folder.

## License

BSD-3-Clause

## Author Information

I am Johannes Kastl, reachable via kastl@b1-systems.de.
