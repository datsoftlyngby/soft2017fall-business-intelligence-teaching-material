# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "bento/ubuntu-16.04"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 8080, host: 8081
  config.vm.network "forwarded_port", guest: 8888, host: 8888
  
  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"
  # config.vm.network "private_network", type: "dhcp"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "../", "/synced_folder"

  # config.vm.provision "file", source: "./serve_playbooks.py", destination: "serve_playbooks.py"

  # The following is adapted from
  # http://stackoverflow.com/a/37335639
  config.vm.provider "virtualbox" do |vb|
    mem_ratio = 1/2
    cpu_exec_cap = 75
    host = RbConfig::CONFIG['host_os']
    # Give VM 3/4 system memory & access to all cpu cores on the host
    if host =~ /darwin/
      cpus = `sysctl -n hw.ncpu`.to_i
      # sysctl returns Bytes and we need to convert to MB
      mem = `sysctl -n hw.memsize`.to_i / 1024^2 * mem_ratio
    elsif host =~ /linux/
      cpus = `nproc`.to_i
      # meminfo shows KB and we need to convert to MB
      mem = `grep 'MemTotal' /proc/meminfo | sed -e 's/MemTotal://' -e 's/ kB//'`.to_i / 1024 * mem_ratio
    elsif host =~ /mingw/
      cpus = `wmic cpu get NumberOfCores`.split("\n")[2].to_i
      mem = `wmic OS get TotalVisibleMemorySize`.split("\n")[2].to_i / 1024 * mem_ratio
    else
      cpus = 1
      mem = 2096128
    end

    if mem == 0
      # Just as a backup in case something went wrong above...
      cpus = 1
      mem = 2096128   
    end

    if cpus == 2
      cpus = 1
    elsif cpus > 2
      cpus = cpus - 2
    end
    
    # puts(mem)
    # puts(mem/1024)
    # puts(mem/1024^2)
    # puts "Provisioning VM with #{cpus} CPU cores (at #{cpu_exec_cap}%) and #{mem/1024} MB RAM."

    vb.customize ["modifyvm", :id, "--memory", mem/1024]
    vb.customize ["modifyvm", :id, "--cpus", cpus]

    vb.customize ["modifyvm", :id, "--cpuexecutioncap", cpu_exec_cap]

    vb.name = "bi2017vm"
    # You might want to include the following for a GUI
    # vb.gui = true
  end

  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    sudo apt-get update

    # sudo echo "LC_ALL=\"en_US.UTF-8\"" >> /etc/environment
    # sudo locale-gen UTF-8

    sudo apt-get install -y git
    sudo apt-get install -y wget

    echo "Installing Anaconda..."
    sudo wget https://repo.continuum.io/archive/Anaconda3-4.4.0-Linux-x86_64.sh -O ~/Anaconda3-4.4.0-Linux-x86_64.sh
    # Anaconda should not be installed as root as earlier...
    bash ~/Anaconda3-4.4.0-Linux-x86_64.sh -b
    
    sudo echo ". $HOME/.bashrc" >> $HOME/.bash_profile
    sudo echo "export PATH=$HOME/anaconda3/bin:$PATH" >> $HOME/.bash_profile
    sudo echo "alias notebook='jupyter notebook --no-browser --ip=0.0.0.0 --NotebookApp.token=\\"\\" --NotebookApp.iopub_data_rate_limit=10000000000'" >> $HOME/.bash_profile

    export PATH="$HOME/anaconda3/bin:$PATH"

    # TODO: chown for /home/ubuntu/anaconda3 or add ubuntu user to group to install packages without sudo
    $(which conda) install -y keras
    $(which conda) install -y basemap
    $(which conda) install -y nltk
    $(which conda) install -y netcdf4

    $(which pip) install suplemon
    $(which pip) install folium
    $(which pip) install osmread


    # this package is necessary for matplotlib to work and not installed by 
    # default
    sudo apt-get install -y libgl1-mesa-glx

    echo "==================================================================="
    echo "=                             DONE                                ="
    echo "==================================================================="
    echo "To log onto the VM:"
    echo "$ vagrant ssh"
    echo "To switch to the directory with teaching material:"
    echo "$ cd /synced_folder/notebooks"
    echo "To start the Jupyter notebook server:"
    echo "$ notebook"
  SHELL
end