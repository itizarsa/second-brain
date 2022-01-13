# Diego Zamboni / mac-setup · GitLab

Source: Notes
Status: Unprocessed
URL: https://gitlab.com/zzamboni/mac-setup

![https://gitlab.com/assets/gitlab_logo-7ae504fe4f68fdebb3c2034e36621930cd36ea87924c11ff65dbcb8ed50dca58.png](https://gitlab.com/assets/gitlab_logo-7ae504fe4f68fdebb3c2034e36621930cd36ea87924c11ff65dbcb8ed50dca58.png)

---

After I received my Mac back with a wiped disk the last time I had to send it in to repair, I decided to more fully automate its setup. I have been using Homebrew for a long time, which makes it easier to reinstall applications and programs I use, but there are many other aspects that could also be automated. In the end, I decided to use the opportunity to brush up my knowledge of Ansible.

This playbook was originally a fork of [https://github.com/AustinCloudGuru/macos-config/](https://github.com/AustinCloudGuru/macos-config/), but has been updated with touches from [https://github.com/geerlingguy/mac-dev-playbook/](https://github.com/geerlingguy/mac-dev-playbook/) and my own personal changes.

# Table of contents

# Configuration

Configuration parameters are read from the files inside `host_vars/127.0.0.1/`. Most of the files in there can be automatically generated from a running system by using the scripts under `scripts/`, and you can run them all automatically by running the `update-vars-files.elv` script (all scripts are written in [Elvish shell](https://elv.sh/)). You can also customize things by hand of course.

Here are the things you need to review and customize before you use it:

- Overall configuration is in the [general-config.yml](https://gitlab.com/zzamboni/mac-setup/-/blob/master/host_vars/127.0.0.1/general-config.yml) file:
    - Review and update the `config_*` variables at the top of the file, which enable/disable the different config modules.
    - If `config_dock` is `yes`, these parameters are relevant:
        - `dockitems_to_persist` (read from [dockitems_to_persist.json](https://gitlab.com/zzamboni/mac-setup/-/blob/master/host_vars/127.0.0.1/dockitems_to_persist.json)) - list of applications that should be in the dock and their order. Any applications that are not in this list will be removed from the Dock).
        - `dock_size` - size of the dock in pixels.
        - `dock_hide` - whether to set the dock to autohide.
    - If `config_terminal` is `yes`, you need to:
        - Store in `files/terminal/` the `.terminal` file for the theme you want to enable.
        - Change `terminal_theme` to the corresponding file name (without the `.terminal` extension).
    - If `config_homebrew_mas` is `yes`, store in `files/Brewfile` the list of taps, formulas, casks and AppStore apps you want to install. **Note:** this can be populated automatically from an existing system using the `scripts/create-homebrew-files.elv` script (this script is written in [Elvish](https://elv.sh/)), or by hand with this command:
        
        ```
        brew bundle --file=files/Brewfile --no-lock --all dump
        
        ```
        
    - `pip_items`, `gem_items`, `npm_items` to the corresponding lists of packages you want to install. Leave them empty if you don’t want to install anything.
    - `git_repos` to the list of git repositories you want to check out, their branches and locations. I use this for my main dotfile directories, and a few others I track. Leave the list empty if you don’t want to clone any repositories.
    - `home_symlinks.json` contains a list of symlinks to set up inside your home directory. I use this to create shortcuts to directories I use inside Dropbox, myCloud and OneDrive. Remove the file or leave the list empty to skip this.
    - If `config_texmf` is `yes`, set the appropriate configuration parameters in the `texmf_params` parameter.
    - If `config_bat` is `yes`, copy your `~/.config/bat/` directory to `files/bat` (this is done automatically by the `scripts/config-files.elv` script).
    - If you want to install [Turbo Boost Switcher](https://www.rugarciap.com/turbo-boost-switcher-for-os-x/) and configure sudo permissions to load/unload its kernel extension without a password, set `config_turboboost` to `yes`.
    - If `config_homefiles` is `yes`, copy any directories and files you want to put under your home directory into `files/homefiles`. Its contents will be copied to your home directory, respecting the directory structure. For example, `files/homefiles/bin/somefile` will be copied to `~/bin/somefile`. You can configure the files and directories you want copied in this directory from your live system in the `scripts/config-files.elv` script.

# Instructions

On a newly-installed Mac, the easiest way to install is to follow the following steps:

1. Make sure you have signed into the Mac App Store. This makes `mas` easier to deal with
2. Install Apples’s command line tools: `xcode-select --install`
3. Install Pip: `sudo easy_install pip`
4. Install Ansible: `sudo pip install ansible`
5. Clone this Repository: `git clone https://gitlab.com/zzamboni/mac-setup`
6. Change into the repo: `cd mac-setup`
7. Install the Ansible requirements: `ansible-galaxy install -r requirements.yml`
8. Edit the files inside `host_vars/127.0.0.1/` as described above.
9. Run the playbook: `ansible-playbook playbook.yml -i inventory -K`

Commands:

```
xcode-select --install
sudo easy_install pip
sudo pip install ansible
git clone https://gitlab.com/zzamboni/mac-setup
cd mac-setup
ansible-galaxy install -r requirements.yml
ansible-playbook playbook.yml -i inventory -K

```

# Keeping the configuration updated

The `scripts/` directory contains a number of scripts that update the configuration files based on the current state on a running system. All these scripts can be executed automatically using the `update-vars-files.elv` script in the top-level directory.

The way I use it is as part of my [topgrade configuration](https://gitlab.com/zzamboni/mac-setup/-/blob/master/files/homefiles/.config/topgrade.toml). Near the end, the following command is executed:

```
"99 Update Ansible config files from running system" = "cd ~/Personal/devel/mac/mac-setup && ./update-vars-files.elv"

```

This automatically updates the Homebrew and MAS application lists, a few other config files, and commits the changes back into git.

# Things still done by hand

Not everything is easy to automate. Here are the things I still had to do by hand the last time around:

- Configure Dropbox, myCloud and OneDrive. The playbook checks whether the corresponding folders are there already and starts up the applications if they are not, but you have to do the config by hand.
- Copy my GPG configuration/key directory `~/.gnupg/` over from my latest backup.
- Copy my [BetterTouchTool](https://folivora.ai/) configuration from my backup:
    - `~/Library/Application Support/BetterTouchTool/`
    - `~/Library/Preferences/com.hegenberg.BetterTouchTool.plist`
    - `~/Library/Preferences/com.hegenberg.BTTRelaunch.plist`
- Set up [Bartender](https://www.macbartender.com/) - I could not figure out which files to copy from my backup to transfer my preferences and license.