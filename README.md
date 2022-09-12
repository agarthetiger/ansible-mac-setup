# ansible-mac-setup

Ansible automation for managing my macOS configuration. This is now used across both MacBook and Mac Mini.

Additional notes here for tools and config which I've not automated.

Shout out to Jeff Geerling for making his [Mac Collection for Ansible](https://github.com/geerlingguy/ansible-collection-mac) open source and his [mac-dev-playbook](https://github.com/geerlingguy/mac-dev-playbook) from which I've borrowed here. 

## Running

```shell
# Run once
ansible-galaxy install -r requirements.yaml

# Run everything, become password is required for p10k role
ansible-playbook configure-mac.yaml --tags roles -K

# Just install pipx packages
ansible-playbook configure-mac.yaml --tags pipx

# Upgrade all brew forumla
ansible-playbook configure-mac.yaml --tags homebrew_formula_update -e update_all_packages=yes

# Uninstall all packages listed for removal
ansible-playbook configure-mac.yaml --tags remove

# Uninstall just ruby gems
ansible-playbook configure-mac.yaml --tags ruby_gems_remove
```

# Dependencies

Gist to be created for bootstrapping script. Ansible needs python to run, python3 needs X-Code developer tools which are not installed on a fresh MacOS install.

The basic steps are as follows
Install xcode developer tools (required for pip/pipx/homebrew)
Download and install
  - Homebrew
  - pipx (via homebrew)
  - ansible (via pipx)
  - VS Code (not strictly necessary as this can be installed by Ansible assuming this playbook needs no edits beforehand)
  - Add config into ~/.zshrc for pipx and completions

# To Do

List of things to improve here include

* Configure default font for iterm2 (via profile?)
* VS Code preferences (not necessarily to be configured by Ansible...) including Editor:Font Family to be MesloLGS NF, ...
* Configure p10k preferences to match current macbook settings
* Review and apply .macos settings
* dotFile management
* kubectl
* Install fonts for lsd, p10k
* Karabiner config?
* Install homebrew and pipx and ansible from a gist or other bootstrapping automation prior to running Ansible
* Testing!

# Troubleshooting

If things don't go well, add or uncomment the debugging lines. See the Ansible [Debugging docs](https://docs.ansible.com/ansible/latest/user_guide/playbooks_debugger.html#available-debug-commands) for the available commands once you hit a debug breakpoint. 

# Non-managed software

* PyCharm

# App Store software

App store apps installed via Jeff Geerling's geerlingguy.mac.mas Collection/Role and the Mac App Store (mas) cli.
Run `mas search <name>` to find the id and name of apps to install. 
