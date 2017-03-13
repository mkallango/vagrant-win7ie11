# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Max time to wait for the guest to shutdown
  config.windows.halt_timeout = 25

  # Admin user name and password
  config.winrm.username = "IEUser"
  config.winrm.password = "Passw0rd!"

  # Configure base box parameters
  config.vm.box = "Win7IE11"
  config.vm.box_url = "./IE11_Win7.box"
  config.vm.guest = :windows

  # Port forward WinRM and RDP
  config.vm.network :forwarded_port, guest: 3389, host: 3389
  config.vm.network :forwarded_port, guest: 5985, host: 5985

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
  end

end