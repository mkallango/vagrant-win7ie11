# -*- mode: ruby -*-
# vi: set ft=ruby :

#require run command below before vagrant up
#  vagrant plugin install vagrant-vbguest 
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
    #config.vm.network :forwarded_port, guest: 3389, host: 3389
    config.vm.network :forwarded_port, guest: 5985, host: 5985
    
    #Solve problem to connect SSH
    config.ssh.username = "IEUser"  
    config.ssh.password = "Passw0rd!"      
    config.ssh.insert_key = false  

    config.vm.provision "shell" do |shell|
        #Turn UAC Off 
        shell.inline = 'C:\Windows\System32\cmd.exe /k %windir%\System32\reg.exe ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System /v EnableLUA /t REG_DWORD /d 0 /f'
        
        #Need to download .NET Framework 4.6 
        #https://download.microsoft.com/download/F/9/4/F942F07D-F26F-4F30-B4E3-EBD54FABA377/NDP462-KB3151800-x86-x64-AllOS-ENU.exe

        #Need to install Oracle Client 11g

        #Need to install Visual Studio 2013 Ultimate or Test Agent to run Automated Tests.
    end

    config.vm.synced_folder ".", "c:/vagrant", disabled: false
end

