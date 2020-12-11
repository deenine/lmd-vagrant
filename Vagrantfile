Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network :private_network, ip: "10.12.14.16"
  config.vm.network :"forwarded_port", guest:5000, host:5000
  config.vm.provider "virtualbox" do |v|
    v.name = "lmd-build-vm-trusty64"
    v.memory = 65536
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "75"]
    v.cpus = 8
  end
  config.vm.provision "ansible" do |ansible|
    ansible.compatibility_mode = "2.0"
    ansible.playbook = "lmd.yml"
    ansible.raw_arguments = ['-T 30', '-e pipelining=True']
  end
end
