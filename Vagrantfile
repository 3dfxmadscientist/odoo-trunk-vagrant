# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  NAME = "odoo-dev"
    
  config.vm.define "odoo" do |odoo|

      odoo.vm.box = "debian75"
      odoo.vm.host_name = NAME

      odoo.vm.provision :shell, :path => "provision.sh"
      odoo.vm.network :forwarded_port, host: 8069, guest: 8069 
      odoo.vm.network :forwarded_port, host: 8070, guest: 80
      odoo.vm.synced_folder "./addons/website", "/usr/lib/pymodules/python2.7/openerp/addons/website"
      odoo.vm.synced_folder "./addons/website_sale", "/usr/lib/pymodules/python2.7/openerp/addons/website_sale"
#      odoo.vm.synced_folder "/Users/xyklex/git/repositories/odoo", "/home/vagrant/odoo"

      odoo.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--memory", "1024"]
        vb.customize ["modifyvm", :id, "--name", NAME ]
      end

#      config.vm.network "public_network", :bridge => 'en0: Ethernet'
  end
end
