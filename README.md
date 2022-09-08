# ansible-mac-setup

Ansible automation for managing my macOS configuration. This is now used across both MacBook and Mac Mini.

Additional notes here for tools and config which I've not automated.

## Running

```shell
# Run everything
ansible-playbook -i localhost, macbook.yaml

# Just install pipx packages
ansible-playbook -i localhost, configure-mac.yaml --tags pipx

# Upgrade all brew forumla
ansible-playbook -i localhost, configure-mac.yaml --tags homebrew_formula_update -e update_all_packages=yes

# Uninstall all packages listed for removal
ansible-playbook -i localhost, configure-mac.yaml  --tags remove

# Uninstall just ruby gems
ansible-playbook -i localhost, configure-mac.yaml  --tags ruby_gems_remove
```

# Dependencies

Gist to be created for bootstrapping script. Ansible needs python to run, python3 needs X-Code developer tools which are not installed on a fresh MacOS install.

The basic steps are as follows
Install xcode (required for pip/pipx/homebrew)
Download and install
  - Homebrew
  - VS Code (might be able to use a package for this, not strictly necessary as this can be bootstrapped in by Ansible)
  - pipx (via homebrew)
  - Add config into ~/.zshrc for pipx and completions

# Upgrading

Run `brew upgrade ansible` to upgrade ansible or `brew ugrade` to upgrade all packages installed via brew.


To upgrade pip once installed use "sudo pip install --upgrade pip"
To upgrade ansible once installed use "sudo pip install ansible==2.3.1.0"

Note that "pip install --upgrade ansible" doesn't take you up to the latest version.
Run "sudo pip install ansible== " [Sic Blank or garbage version] to list available
Ansible versions.

# What needs doing

List of things to improve here include

* Review and apply .macos settings
* dotFile management
* kubectl
* Install fonts for lsd, p10k
* Karabiner config?
* Testing!

# Non-managed software

* PyCharm

# App Store software

* SSH Tunnel
* Coca
* Magnet
* Toad
* MockSMTP
* Pixelmator
* OhMyStar2
