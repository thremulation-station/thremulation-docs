# Installation


## Getting Requirements
Following the installation steps for your host platform. If you don't see your OS flavor, consider [contributing](#).


=== "macOS"
  
      1. Install the [Homebrew](https://brew.sh/) package manager
      1. Update brew: `brew update`
      1. Install remaining requirements. You can copy / paste the following into your terminal:
            ```sh
            brew cask install virtualbox vagrant

            brew install ansible git

            vagrant plugin install vagrant-disksize
            vagrant plugin install vagrant-vbguest
            ```


=== "Windows10"
  
      1. If you're on a Windows box, we recommend using [Chocolatey](https://chocolatey.org/) for package management.
      1. Install remaining requirements. You can copy / paste the following into your terminal:
            ```pwsh
            choco install virtualbox vagrant

            choco install ansible git

            vagrant plugin install vagrant-disksize
            vagrant plugin install vagrant-vbguest
            ```
      > Note: Vagrant requires a restart as part of the installation.

=== "Linux (RHEL)"

      1. This section assumes that you're using a RHEL-based distro, preferrably Centos 7. All commands assume a root shell (`sudo -s`).
      
      1. Install requirements
            ```sh
            yum groupinstall -y "Development Tools"

            yum install -y \
            kernel-devel \
            kernel-devel-3.10.0-1127.el7.x86_64 \
            epel-release \

            yum install -y ansible
            ```
      1. Install VirtualBox  
      a. `curl -o /etc/yum.repos.d/virtualbox.repo http://download.virtualbox.org/virtualbox/rpm/rhel/virtualbox.repo`  
      b. `rpm --import https://www.virtualbox.org/download/oracle_vbox.asc`  
      c. `yum install -y VirtualBox-6.0`      
      1. Install Vagrant  
      a. `yum install -y https://releases.hashicorp.com/vagrant/2.2.10/vagrant_2.2.10_x86_64.rpm`  
      b. `vagrant plugin install vagrant-disksize`  
      c. `vagrant plugin install vagrant-vbguest`  




## Getting the Project

Now that you have git installed, you can clone the project locally:  

1. $ `git clone https://github.com/thremulation-station/thremulation-station.git`
