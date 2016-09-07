# puppet-practice
This is a demonstration puppet configuration using 1 Ubuntu Trusty (14.04) server and 2 Cumulus Linux 3.1 switches.
The Ubuntu server (server-pup-mstr) will be the Puppet Master and Cumulus switches, switch1-pup-agent and switch2-pup-agent 
will run Puppet agents and can be provisioned by the Puppet Master.

Steps:

1) Bring all the systems up with "Vagrant up"

2) Login to switch1-pup-agent and switch2-pup-agent and run this command:  "sudo /opt/puppetlabs/bin/puppet agent -t"

3) Login to server-pup-mstr and run these commands:  
  
  "sudo puppet cert sign switch1-pup-agent"
  
  "sudo puppet cert sign switch2-pup-agent"
  
  Verify that puppetserver is running with command:  service puppetserver status

4) Login to switch1-pup-agent and switch2-pup-agent again and re-run the command:  "sudo /opt/puppetlabs/bin/puppet agent -t"

You should now be ready to build your Puppet configuration.

