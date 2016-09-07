#  A Vagrant file that will create some Cumulus OS switches.
#  1st Switch (switch-pup-mstr) will be the puppet master
#  The 2nd switch (switch-pup-agent) will be running puppet agent
#
#  Srivats Iyer, Cumulus Networks, 9/6/2016
#


Vagrant.configure(2) do |config|

   config.vm.box = "cumulus-vx-3.1.0"
  

##### DEFINE VM for server-pup-mstr (Puppet Master running Ubuntu  #####
   config.vm.define "server-pup-mstr" do |override|
    
     override.vm.box = "ubuntu/trusty64" 
     override.vm.network "private_network", ip: "192.168.100.1/24"     
 
     override.vm.provider "virtualbox" do |v|
       v.name = "server-pup-mstr"
       v.memory = 4096 
     end   
  
   end


##### DEFINE VM for switch1-pup-agent (Puppet Agent Switch 1)  #####
   config.vm.define "switch1-pup-agent" do |device|
     device.vm.hostname = "switch1-pup-agent"

     # Internal network for swp* interfaces.
     device.vm.network "private_network", virtualbox__intnet: "swp1"
     device.vm.network "private_network", virtualbox__intnet: "swp2"
     device.vm.network "private_network", ip: "192.168.100.2/24" 
     device.vm.network "private_network", virtualbox__intnet: "swp4"

     device.vm.provider "virtualbox" do |v|
       v.name = "switch1-pup-agent"
       v.memory = 512
     end

   end

##### DEFINE VM for switch2-pup-agent (Puppet Agent Switch)  #####
   config.vm.define "switch2-pup-agent" do |device|
     device.vm.hostname = "switch2-pup-agent"

     # Internal network for swp* interfaces.
     device.vm.network "private_network", virtualbox__intnet: "swp1"
     device.vm.network "private_network", virtualbox__intnet: "swp2"
     device.vm.network "private_network", ip: "192.168.100.3/24" 
     device.vm.network "private_network", virtualbox__intnet: "swp4"

     device.vm.provider "virtualbox" do |v|
       v.name = "switch2-pup-agent"
       v.memory = 512
     end

   end


   #config.vm.provision "ansible" do |ansible|
   #  ansible.verbose = "vvv"
   #  ansible.playbook = "pup-playbook.yml"
   #end

   puts "The value of config is %s: " % [config]

end

#Vagrant.configure(2) do |ansible|
#   ansible.verbose = "vvv"
#   ansible.playbook = "pup-playbook-post-up.yml"
#end


