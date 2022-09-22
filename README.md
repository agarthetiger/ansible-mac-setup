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

# Dependencies

There are dependencies between configuration in here and in my dotfiles. It's not going to be simple or pratcial IMO to decouple them. For example, the diodonfrost.p10k role installs the MesloLGS NF font which is also set as the default font in my iterm2 profile (Default.json). Also, I configure a bunch of tools in my dotfiles, specifically in .zshrc, which are dependent on other packages being installed. My dotfiles are in a separate repo but the package installs are here.
I currently have no requirement which warrants the time and effort to unpick and test these as separately managed components.

# iterm2 profiles

See https://iterm2.com/documentation-dynamic-profiles.html
I should diff the file I've just added with an export from another Mac to see if the GUIDs match and what the differences are. I should probably strip this file down to just the elements which I've changed vs the Default profile, which is the font and maybe the ASCII blue colour.

Dumping the file into ~/Library/Application Support/iterm2/Dynamic Profiles is the easy option. Automating iTerm2 with it's python api would be the first-class solution if I can justify the time to do it. See https://iterm2.com/python-api/profile.html

# Karabiner elements configuration

See https://karabiner-elements.pqrs.org/docs/manual/operation/export/

# vi(m) configuration

To do. See https://github.com/vim-airline/vim-airline or https://github.com/powerline/powerline , either of which would be awesome. I'm not big on doing much with vim, especially on MacOS but this would be useful on a Raspberry Pi with the Lite OS, like my Pi Zeros.

# Fonts

I might need (or like) more fonts, see here for many powerline fonts. https://github.com/powerline/fonts
