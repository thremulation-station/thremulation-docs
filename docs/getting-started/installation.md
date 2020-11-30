# Installation
The following 3 platforms have been tested as a working host platform:
- macOS
- Windows10
- Linux (rpm-based)

<details>
  <summary>macOS Setup</summary>
  
  1. Install and Update Homebrew
        * It is recommended to use [Homebrew](https://brew.sh/) which simplifies package management and installation for all requirements
        * Follow the instructions at the above link to use the "one-liner" install method.
        * Update brew: `brew update`
  1. Install remaining requirements. You can copy / paste the following into your terminal:

        ```sh
        brew cask install virtualbox vagrant

        brew install ansible git

        vagrant plugin install vagrant-disksize
        vagrant plugin install vagrant-vbguest
        ```
  1. Clone the Project
        * `git clone https://github.com/mocyber/ThreatEmulation-DetectionLab.git`
</details>

<details>
  <summary>Windows Setup</summary>
  
  1. Install and Update Homebrew
        * It is recommended to use [Chocolatey](https://chocolatey.org/) which simplifies package management and installation for all requirements
        * Follow the instructions at the above link to use the "one-liner" install method.
  1. Install remaining requirements. You can copy / paste the following into your terminal:

        ```sh
        choco install virtualbox vagrant
        ```
        Vagrant requires a restart as part of the installation.
        ```sh
        choco install ansible git

        vagrant plugin install vagrant-disksize
        vagrant plugin install vagrant-vbguest
        ```
  1. Clone the Project
        * `git clone https://github.com/mocyber/ThreatEmulation-DetectionLab.git`
</details>

<details>
  <summary>Linux Setup</summary>
  <br>

  This section assumes that you're using a RHEL-based distro, preferrably 
  **Centos 7**. All commands assume a root shell (`sudo -s`).
  
  1. Install requirements
        ```sh
        yum groupinstall -y "Development Tools"

        yum install -y \
        kernel-devel \
        kernel-devel-3.10.0-1127.el7.x86_64 \
        epel-release \

        yum install -y ansible
        ```
  
  1. Install Vagrant
        * `yum install -y https://releases.hashicorp.com/vagrant/2.2.10/vagrant_2.2.10_x86_64.rpm`
        * `vagrant plugin install vagrant-disksize`
        * `vagrant plugin install vagrant-vbguest`

  1. Install VirtualBox
        * `curl -o /etc/yum.repos.d/virtualbox.repo http://download.virtualbox.org/virtualbox/rpm/rhel/virtualbox.repo`
        * `rpm --import https://www.virtualbox.org/download/oracle_vbox.asc
        * `yum install -y VirtualBox-6.0`

  1. Clone the Project
        * `git clone https://github.com/mocyber/ThreatEmulation-DetectionLab.git`
</details>


## Building the Range
Once all the tools have been install, it's time to build the local range.

1. Move into this repo's vagrant directory: `cd ThreatEmulation-DetectionLab/vagrant`

1. Kick of the import / build / provisioning of all machines: `vagrant up`

1. Get yourself some :coffee: , this will take a sec

> By a "sec", @seven62 means like 15-20 min. Drink you cup very very slowly.


## Initial Access

This lab environment is designed for users to execute and detect threats by interacting with 2 primary interfaces:

1. **Kibana WebUI**

- to reach Kibana browse to `localhost:5601`

        Kibana Credentials
        user: vagrant
        pass: vagrant

- once in Kibana click the 3 hash dropdown menu in the upper left corner of the UI and select the "Discover" tab.

> Ensure that the timepicker is set to the most recent timeframe, example "Last 24 hours".

1. **Atomic Redteam**

This adversary emulation toolset is accessed by sshing into the "elastic" box and starting a powershell session.

- ssh to the elastic vbox:
    - $`vagrant ssh elastic`
- start a powershell session
    - $`pwsh`