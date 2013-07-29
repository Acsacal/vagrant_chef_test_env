Vagrant.configure("2") do |config|
  config.vm.box = "precise64"

  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  
  config.vm.hostname = "some-box"
  
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", 376]
    vb.customize ["modifyvm", :id, "--cpus", 1]
  end

  config.vm.network :private_network, ip: "10.1.1.111"

  config.vm.synced_folder "www/", "/var/www"

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "recipes/cookbooks"
    chef.roles_path = "recipes/roles"
    chef.add_role "web"
    chef.data_bags_path = "../my-recipes/data_bags"
  
    chef.json = {

      "mysql" => {
        "server_root_password" => "%your_path0%",			
			  "server_repl_password" => "%your_path1%",
			  "server_debian_password" => "%your_path2%"
      }
	}
  end
end
