Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network :private_network, ip: "10.12.14.16"
  config.vm.synced_folder "build/", create: true, mount_options: ["dmode=777,fmode=755"]
  config.vm.provider "virtualbox" do |v|
    v.name = "lmd-build-vm-trusty64"
    v.memory = 2048
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "75"]
    v.cpus = 1
  end
  config.vm.provision "ansible" do |ansible|
    ansible.compatibility_mode = "2.0"
    ansible.playbook = "lmd.yml"
    ansible.raw_arguments = ['-T 30', '-e pipelining=True']
  end
end
