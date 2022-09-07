# ansible-mac-setup

My portable automated configuration script using Ansible for managing my mac packages, tools, bash defaults etc.

# Dependencies

Ansible installation is required first. I've dropped pip in favour of homebrew for package installation due to continued headaches with mutating infrastructure (ie. things that used to work no longer do).

# Upgrading
Run `brew upgrade ansible` to upgrade ansible or `brew ugrade` to upgrade all packages installed via brew.


To upgrade pip once installed use "sudo pip install --upgrade pip"
To upgrade ansible once installed use "sudo pip install ansible==2.3.1.0"

Note that "pip install --upgrade ansible" doesn't take you up to the latest version.
Run "sudo pip install ansible== " [Sic Blank or garbage version] to list available
Ansible versions.

# What needs doing
List of things to improve here include
* Creating separate roles for specific items
* Add in clone and setup for my dotFiles
* 

Non-managed software
====================

* Fork - https://git-fork.com/
* Sublime Text
* Beyond Compare
* Docker
* Kitematic
* Kiwi for Gmail 
* Vagrant
* Packer
* IntelliJ IDEA
* PyCharm
* Atom

App Store software
==================
* SSH Tunnel
* Coca
* Magnet
* Toad
* MockSMTP
* Pixelmator
* OhMyStar2
