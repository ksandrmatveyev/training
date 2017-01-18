Vagrant.configure("2") do |config|
	config.vm.box = "bertvv/centos72"
	# if you get esync error use instruction below
	# config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
	config.vm.define "server1" do |server1|
		server1.vm.hostname="gitdevserv"
		# server1.vm.network "forwarded_port", guest: 80, host: 8083
		server1.vm.network "private_network", ip: "172.20.20.10"
		server1.vm.provision "netw", run: "always", type: "shell", inline: "sudo nmcli connection reload && sudo systemctl restart network.service"
		server1.vm.provision "get_git", type: "shell", inline: "sudo yum install git -y"
	end
=begin	
	config.vm.define "server2" do |server2|
		server2.vm.hostname="server2"
		# server2.vm.network "forwarded_port", guest: 80, host: 8084
		server2.vm.network "private_network", ip: "172.20.20.11"
		server2.vm.provision "netw", type: "shell", path: "int.sh"
	end
=end
end
