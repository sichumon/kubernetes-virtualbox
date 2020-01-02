Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/bionic64"  # Default box
    config.ssh.forward_agent = true

    # Set Master machine
    config.vm.define "master" do |master|
        master.vm.network "private_network", ip: "192.168.56.10"
        master.vm.hostname = "master"

        # Set vm name
        master.vm.provider :virtualbox do |vb|
            vb.name = "master  - 192.168.56.10"
        end

        # Run ansible playbook
        master.vm.provision "ansible_local" do |ansible|
            ansible.become = true
            ansible.playbook = "ansible-playbooks/master.yml"
        end
    end

    # Set Node 1
    config.vm.define "node_1" do |node_1|
        node_1.vm.network "private_network", ip: "192.168.56.11"
        node_1.vm.hostname = "node1"

        node_1.vm.provider :virtualbox do |vb|
            vb.name = "node1 - 192.168.56.11"
        end

        node_1.vm.provision "ansible_local" do |ansible|
            ansible.become = true
            ansible.playbook = "ansible-playbooks/common.yml"
        end
    end
end