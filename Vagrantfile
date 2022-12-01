Vagrant.configure("2") do |config|
    config.vm.box = "debian/bullseye64"
    HOSTNAME = "subject-registration"
    CPU = 2
    RAM = 4096
    IP = "192.168.58.111"

    config.ssh.username = "vagrant"
    config.vm.network :private_network, ip: IP
    config.vm.hostname = HOSTNAME

    config.hostsupdater.aliases = {
      IP => [
        HOSTNAME
      ],
    }

    config.vm.provider :virtualbox do |vb|
        # Use VBoxManage to customize the VM. For example to change memory:
        vb.customize [
          'modifyvm', :id,
          '--natdnshostresolver1', 'on',
          '--memory', RAM.to_s,
          '--cpus', CPU.to_s
        ]
    end

    config.vm.provider :libvirt do |libvirt|
        libvirt.cpus = CPU
        libvirt.memory = RAM
    end
end
