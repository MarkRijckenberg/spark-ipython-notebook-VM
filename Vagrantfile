# -*- mode: ruby -*-
# vi: set ft=ruby :
# Prerequisites for host operating system:
# [Ubuntu 14.04 LTS 64-bit or newer] or [Windows 7 64-bit or newer]
# Mac OS X might be supported as well, but not tested yet
# curl (http://www.confusedbycode.com/curl/)
# git (https://git-scm.com/download/)
# vagrant 1.7.2 or newer (https://www.vagrantup.com/downloads.html)
# Virtualbox 4.3.28 or newer (with shared folder support enabled) (http://dlc-cdn.sun.com/virtualbox/4.3.28/index.html)


ipythonPort = 8001                 # Ipython port to forward (also set in IPython notebook config)

Vagrant.configure(2) do |config|
  config.ssh.insert_key = true
  config.vm.define "sparkvm" do |master|
    master.vm.box = "sparkmooc/base"
    master.vm.network :forwarded_port, host: ipythonPort, guest: ipythonPort, auto_correct: true   # IPython port (set in notebook config)
    master.vm.network :forwarded_port, host: 4040, guest: 4040, auto_correct: true                 # Spark UI (Driver)
    master.vm.hostname = "sparkvm"
    master.vm.usable_port_range = 4040..4090

    master.vm.provider :virtualbox do |v|
      v.name = master.vm.hostname.to_s
    end
  end
end
