Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  
  # MySQL
  config.vm.network "forwarded_port", guest: 3306, host: 3306

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "playbook_root.yml"
    ansible.verbose = "vvvv"
    ansible.sudo = true
  end
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.verbose = "vvvv"
  end
end
