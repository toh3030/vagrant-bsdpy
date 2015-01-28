# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "chef/debian-7.8"

  # specifying a MAC address is optional - in this case I have a DHCP
  # whitelist in place
  config.vm.network "public_network", :mac => "000C29B8B597"

  # use rsync because running the kernel NFS server off a vmware
  # shared folder doesn't really work
  config.vm.synced_folder "./nbi", "/nbi", type: "rsync",
    # only change here from Vagrant defaults is we leave out the --copy-links
    # option, because NBIs from DeployStudio will contain a relative symlink
    # for NetInstall.dmg
    rsync__args: ["--verbose", "--archive", "--delete", "-z"],
    rsync__exclude: ".git/"

  config.vm.provision "shell", path: "scripts/setup.sh"
end