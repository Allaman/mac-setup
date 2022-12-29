## Mac Setup

⚙️ Automatic configuration for my Mac.

ℹ️ Blog post about [moving to macOS](https://rootknecht.net/blog/moving-to-macOS/) after ten years of Linux.

Automatic installation is based upon the following [Ansible](https://www.ansible.com/) roles:

- [geerlingguy.homebrew](https://github.com/geerlingguy/ansible-collection-mac/tree/master/roles/homebrew) manages homebrew installation and packages
- [geerlingguy.mas](https://github.com/geerlingguy/ansible-collection-mac/tree/master/roles/mas) manages apps from the app store
- [ansible-role-binaries](https://github.com/Allaman/ansible-role-binaries) installs binaries
- [ansible-role-shell](https://github.com/Allaman/ansible-role-shell) configures my shell
- [ansible-role-pip](https://github.com/Allaman/ansible-role-pip) installs pip packages

Also kudos to [Jeff Geerling](https://www.jeffgeerling.com/) for his work with [mac-dev-playbook](https://github.com/geerlingguy/mac-dev-playbook) which obviously influenced my setup.

## Bootstrap

Bootstrap your system to be able to run Ansible:

- `xcode-select --install`
- `export PATH=$PATH:$HOME/Library/Python/3.8/bin:/opt/homebrew/bin`
- `pip3 install --upgrade pip`
- `pip3 install --user ansible`

## Run Ansible

Run Ansible with the provided Makefile:

- `make install` to download required ansible roles
- `make configure` to run `ansible-playbook` (sudo password required)

## Manual installation

Some apps need to be installed manually

- Download [TinkerTool](https://www.bresink.biz/download2.php?ln=1&dl=TinkerTool&MBSKey=2b2ed27cad1c358503aac7223b8d345f) for some extra tweaks
- Chromium cask not working as expected -> [download](https://download-chromium.appspot.com/?platform=Mac_Arm&type=snapshots) manually and run `xattr -cr /Applications/Chromium.app`
- Download and install [FastRAWViewer](https://www.fastrawviewer.com/)
- Download and install a patched [font](https://github.com/shaunsingh/SFMono-Nerd-Font-Ligaturized) for your terminal

## Configuration

Configuration is mainly done via my [dotfiles](https://github.com/Allaman/dots) repo and a private dotfiles repo using [chezmoi](https://www.chezmoi.io/)

## Replace Finder with Forklift3

```sh
defaults write -g NSFileViewer -string com.binarynights.ForkLift-3;
defaults write com.apple.LaunchServices/com.apple.launchservices.secure LSHandlers -array-add '{LSHandlerContentType="public.folder";LSHandlerRoleAll="com.binarynights.ForkLift-3";}'
```
