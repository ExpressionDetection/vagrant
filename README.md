# Vagrant setup

This is the setup repository for the [Spoiled](https://gitlab.com/spoiled) project. It contains a `Vagrantfile` with the VM setup for this system.

## Getting Started

* Install [Virtual Box](https://www.virtualbox.org/wiki/Download_Old_Builds_6_0) version `6.0`

* Install [Vagrant](https://www.vagrantup.com/)

* For **Windows users only**
    * Disable Hyper-V by running `bcdedit /set hypervisorlaunchtype off` as administrator
    * Reboot your machine

* Run `vagrant up --provision`
    * This will build your development VM

* Run `vagrant ssh` to get inside of it afterwards
    * Password is `vagrant`

* Clone [Compose](https://gitlab.com/spoiled/compose) by:
    * Copy the `~/.ssh/id_ed25519.pub` key content to [GitLab key settings](https://gitlab.com/profile/keys).
    * `cd /projects`
    * `git clone git@gitlab.com:spoiled/compose.git`
    * `cd compose`
    * Follow the `README` inside [Compose](https://gitlab.com/spoiled/compose)

## Configuring Visual Code Remote

* Execute `vagrant ssh-config`
    * Change `User` to `root` and `PasswordAuthentication` to `yes`

* Add the configuration to your `~/.ssh/config` file

* Install VS Code `Remote - SSH` extension

* Click on the extension menu and enjoy!

## Helpful commands

* Turn off the VM: `vagrant halt`
* Turn on the VM: `vagrant up`
* Turn provision VM resources: `vagrant up --provision`
* Destroy a VM: `vagrant destroy`
