# Vagrant setup

This is the setup repository for the [ExpressionDetection](https://github.com/ExpressionDetection) project. It contains a `Vagrantfile` with the VM setup for this system.

## Getting Started

* Install [Virtual Box](https://www.virtualbox.org/wiki/Download_Old_Builds_6_0) version `6.0` or greater

* Install [Vagrant](https://www.vagrantup.com/)

* For **Windows users only**
    * Disable Hyper-V by running `bcdedit /set hypervisorlaunchtype off` as administrator
    * Reboot your machine

* Run `mkdir ~/ExpressionDetectionChromeExtension` to create a folder to host all repositories
    * This folder will be in sync with the VM

* Run `vagrant up --provision`
    * This will build your development VM

* Run `vagrant ssh` to get inside of it afterwards
    * Password is `vagrant`

* Clone [Compose](https://github.com/ExpressionDetection/compose) by:
    * Copy the `~/.ssh/id_ed25519.pub` key content to [Github key settings](https://github.com/settings/keys).
    * `cd /projects`
    * `git clone git@github.com:ExpressionDetection/compose.git`
    * `cd compose`
    * Follow the `README` inside [Compose](https://github.com/ExpressionDetection/compose)

## Configuring Visual Code Remote

* Execute `vagrant ssh-config`
    * Change `User` to `root` and `PasswordAuthentication` to `yes`

* Add the configuration to your `~/.ssh/config` file

* Install VS Code `Remote - SSH` extension

* Click on the extension menu and enjoy!
    * Password is `vagrant`

## Helpful commands

* Turn off the VM: `vagrant halt`
* Turn on the VM: `vagrant up`
* Turn provision VM resources: `vagrant up --provision`
* Destroy a VM: `vagrant destroy`
