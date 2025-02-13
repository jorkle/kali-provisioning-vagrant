Vagrant.configure("2") do |config|
    config.vm.box = "kalilinux/rolling"
    config.vm.box_version = "2024.4"
    config.vm.provider "vmware_desktop" do |v|
      v.gui = true
      v.vmx["memsize"] = "8192"
      v.vmx["numvcpus"] = "6"
      v.force_vmware_license = "workstation"
    end
    config.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "ansible/main.yml"
        ansible.install_mode = "pip"
        ansible.pip_install_cmd = "sudo apt install python3-pip -y"
        ansible.galaxy_role_file = 'ansible/requirements.yml'
        ansible.pip_args = "--upgrade --break-system-packages"
    end
end
