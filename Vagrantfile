Vagrant.configure("2") do |config|
    config.vm.box = "geerlingguy/ubuntu2004"

    config.ssh.insert_key = false
   
     config.vm.provision "ansible" do |ansible|
       ansible.verbose = "vv"
       ansible.playbook = "playbook.yml"
     end
   end