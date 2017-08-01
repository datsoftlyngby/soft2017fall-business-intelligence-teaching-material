# What is this?

The `Vagrantfile` in this folder specifies the virtual machine (VM), which you will use throughout the semester in the Business Intelligence course. The VM contins an Ubuntu Linux -Ubuntu 16.04 LTS (Xenial Xerus)- and a Python 3.6 installation (via the Anaconda distribution). Actually, it is the same in which you just see this lecture's material.

## Getting started with Vagrant

In the following is a step by step guide to get you up and running.

  * Download and install VirtualBox (https://www.virtualbox.org/wiki/Downloads)
  * Download and install Vagrant (https://www.vagrantup.com/downloads.html)
    * To get started with Vagrant on Windows, see https://www.sitepoint.com/getting-started-vagrant-windows/ Focus in particular on using PuTTY instead of SSH on Windows
or alternatively install Git on Windows and follow the directions: http://stackoverflow.com/a/16247703
    * On Unix'ish operating systems, if you did not already generate an SSH keypair, generate one (e.g., via `ssh-keygen -t rsa`)
  * Clone the infrastructure project into a directory of your choice (`/path/to/`):

    ```
    git clone https://github.com/datsoftlyngby/soft2017fall-business-intelligence-teaching-material.git 
    ```

  * On the command line change directory to where you cloned this repository (`/path/to/cloned/repo/vm`). Likely, it is just:
  
    ```bash
    cd ./soft2017fall-business-intelligence-teaching-material/vm
    ```
  * Subsequently, start up the VM, which will take a bit on the first start up as it has to download the Ubuntu image and a bit of other software.
    ```bash
    vagrant up
    ```
  * To log onto the virtual machine (VM) execute
    ```bash
    vagrant ssh
    ```
  * Now you can start the Jupyter Notebook server (to program in the browser) via:
    ```bash
    vagrant@vagrant:~$ cd /synced_folder/lecture_notes
    vagrant@vagrant:~$ notebook
    ```
    **Note** The `notebook` command is just an alias to the complete command `jupyter notebook --no-browser --ip=0.0.0.0 --NotebookApp.token=""` The `notebook` command is context sensitive. That is, the server is always started in the scope of the current directory. When you have your notebooks stored in another directory than the one in which you execute `notebook`, then you have change directories before.
    
  * Now you should be able to connect to the Jupyter Notebook server by connecting to http://localhost:8888 in the browser of your choice. 
  * In case you are done working on your virtual machine, you can leave it by issuing the `exit` command. Subsequently, you can put the virtual machine to "sleep" (just like closing the lid of your notebook) by running `vagrant suspend` on your host machine.

    ```bash
    vagrant@vagrant:~$ exit
    vagrant suspend
    ```

  * In case you want to discard this VM just run `vagrabt destroy` from within the `./soft2017fall-business-intelligence-teaching-material/vm` directory.