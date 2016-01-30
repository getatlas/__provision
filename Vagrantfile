# Setting up this machine requires Ansible 2.0
# http://docs.ansible.com/ansible/intro_installation.html#getting-ansible

Vagrant.require_version ">= 1.7.0"

Vagrant.configure(2) do |config|

    provider = (ARGV[2] || ENV['VAGRANT_DEFAULT_PROVIDER'] || :parallels).to_sym

    if provider == :parallels
        # The parallels provider is significantly better on OS X
        # However, it is not free (Version 11+)
        # You can use VirtualBox if you wish
        # Read this to get started: http://parallels.github.io/vagrant-parallels/docs/getting-started.html
        config.vm.provider :parallels do |p|
            config.vm.box = "parallels/ubuntu-14.04"
            p.name = "Atlas Development Machine"
            p.linked_clone = true
            p.update_guest_tools = true

            p.memory = 2048 # 2 GB of memory by default - Change if necessary
            p.cpus = 2 # 2 CPU cores by default - Change if necessary
        end
    end

    if provider == :virtualbox
        config.vm.provider :virtualbox do |vb|
            config.vm.box = "ubuntu/trusty64"
            vb.name = "Atlas Development Machine"
        end
    end

    config.vm.post_up_message = "For contributing advice: https://github.com/getatlas/atlas/wiki/Contributing. Server IP: 192.168.55.77"

    config.vm.synced_folder "../source", "/var/www/vhosts/atlas"

    config.vm.network "private_network", ip: "192.168.55.77"

    config.vm.provision "ansible" do |ansible|
        ansible.inventory_path = "./ansible/inventory"
        ansible.limit = "vagrant"
        ansible.playbook = "./ansible/playbook.yml"
    end
end
