Vagrant.configure("2") do |config|
    #config.vm.box = "cdaf/WindowsServerDC"
    #config.vm.box_version = "2020.05.14"
    config.vm.box = "danielmenezesbr/WindowsServerDC"
    
    config.winrm.username = "vagrant"
    config.winrm.password = "vagrant"
    config.vm.guest = :windows
    config.vm.communicator = "winrm"
    config.winrm.timeout = 1800 # 30 minutes
    config.winrm.max_tries = 20
    config.winrm.retry_limit = 200
    config.winrm.retry_delay = 10
    config.vm.graceful_halt_timeout = 600

    config.vm.define 'ubuntu'

    # Vagrant boot needs more time on AppVeyor (see https://help.appveyor.com/discussions/problems/1247-vagrant-not-working-inside-appveyor)
    config.vm.boot_timeout = 3600

    # Prevent SharedFoldersEnableSymlinksCreate errors
    config.vm.synced_folder ".", "/vagrant", disabled: true

    config.vm.provider :virtualbox do |vb|
        vb.name = 'ubuntu'
        vb.memory = 2048
        vb.cpus = 2
        # Vagrant needs this config on AppVeyor to spin up correctly (see https://help.appveyor.com/discussions/problems/1247-vagrant-not-working-inside-appveyor)
        #vb.customize ["modifyvm", :id, "--nictype1", "Am79C973"]
        #vb.customize ['modifyvm', :id, '--cableconnected1', 'on']
        vb.gui = true
    end
end
