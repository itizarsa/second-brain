# minamarkham/formation: 💻 macOS setup script for front-end development

Source: Website
Status: Unprocessed
URL: https://github.com/minamarkham/formation

[https://opengraph.githubassets.com/f24c8b9c4f7c05a04f45710ae142feef49c67f9a955544f4e633cb534761f48a/minamarkham/formation](https://opengraph.githubassets.com/f24c8b9c4f7c05a04f45710ae142feef49c67f9a955544f4e633cb534761f48a/minamarkham/formation)

---

# Formation

![minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/1f41d.png](minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/1f41d.png)

[minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/68747470733a2f2f63352e70617472656f6e2e636f6d2f65787465726e616c2f6c6f676f2f6265636f6d655f615f706174726f6e5f627574746f6e4032782e706e67](minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/68747470733a2f2f63352e70617472656f6e2e636f6d2f65787465726e616c2f6c6f676f2f6265636f6d655f615f706174726f6e5f627574746f6e4032782e706e67)

![minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/formation.gif](minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/formation.gif)

> Formation is a shell script to set up a macOS laptop for design and development.
> 

It can be run multiple times on the same machine safely. It installs, upgrades, or skips packages based on what is already installed on the machine.

## Install

Download the script:

```
git clone git@github.com/minamarkham/formation.git && cd formation
```

Review the script (please don't run scripts you don't understand):

```
less slay
```

Slay:

```
cd formation
./slay 2>&1 | tee ~/slay.log
```

Just follow the prompts and you’ll be fine.

![minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/1f44c.png](minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/1f44c.png)

![minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/26a0.png](minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/26a0.png)

Warning: I advise against running [this script](https://github.com/minamarkham/formation/blob/master/slay) unless you understand what it’s doing to your computer.

I created this based on my own preferences; your mileage may vary.

Once the script is done, quit and relaunch Terminal.

It is highly recommended to run the script regularly to keep your computer up to date.

Your last Formation run will be saved to `~/slay.log`. To review it, run `less ~/slay.log`.

That's it!

![minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/2728.png](minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/2728.png)

## What it sets up

The setup process will install:

Basic tools:

- [XCode Command Line Tools](https://developer.apple.com/xcode/downloads/) for developer essentials.
- [Bash-it](https://github.com/Bash-it/bash-it/), for a more powerful bash.
- [Git](https://git-scm.com/) for version control
- [Homebrew](http://brew.sh/) for managing operating system libraries.

Package Managers:

- [NVM](https://github.com/creationix/nvm/) for managing and installing multiple versions of [Node.js](http://nodejs.org/) and [npm](https://www.npmjs.org/)
- [Rbenv](https://github.com/sstephenson/rbenv) for managing versions of Ruby
- [Yarn](https://yarnpkg.com/en/) for managing JavaScript packages

CLI Tools & Utilities:

- [asciinema](https://asciinema.org/) for recording terminal sessions
- [Gulp](https://gulpjs.com/) the streaming build system
- [Hotel](https://github.com/typicode/hotel), a simple process manager for developers
- [Hub](http://hub.github.com/) for interacting with the GitHub API
- [hugo](https://gohugo.io/), an open-source static site generator
- [ImageMagick](http://www.imagemagick.org/) to create, edit, compose, or convert bitmap images
- [mas](https://github.com/mas-cli/mas) Mac App Store command line interface
- [Tig](https://github.com/jonas/tig) text-mode interface for git
- [Vagrant](https://www.vagrantup.com/) for development environments

### Apps

Productivity

- [Airmail](http://airmailapp.com/) for a better mail client.
- [Alfred](https://www.alfredapp.com/) for increased productivity and efficiency with macOS.
- [Fantastical](https://flexibits.com/fantastical) for a better calendar.
- [Things](https://culturedcode.com/things/) for getting things done.

Development

- [Dash](https://kapeli.com/dash) offline access to API documentation sets
- [ForkLift](https://www.binarynights.com/forklift/) FTP client
- [Hyper](https://hyper.is/) for an alternative terminal.
- [ImageOptim](https://imageoptim.com/mac) for image optimization.
- [iTerm](https://www.iterm2.com/) for a better terminal.
- [Kaleidoscope](https://www.kaleidoscopeapp.com/) for a better diff tool.
- [Virtual Box](https://www.virtualbox.org/) powerful virtualization tool
- [Visual Studio Code](https://code.visualstudio.com/) IDE

Design

- [Affinity Designer](https://affinity.serif.com/en-us/designer/)
- [Affinity Photo](https://affinity.serif.com/en-us/photo/)
- [Sip](http://sipapp.io/) collect, organize & share your colors
- [Sketch](https://www.sketchapp.com/) for design.

Communication

- [Bear](http://www.bear-writer.com/) for writing and previewing markdown.
- [Skype](https://www.skype.com/en/) for free calls to friends and family.
- [Slack](https://slack.com/) where work happens.
- [Ulysses](https://ulyssesapp.com/) for long-form writing.

Utilities

- [1Password](https://1password.com/) for password management.
- [Dropbox](https://www.dropbox.com/) for cloud file storage.
- [Divvy](http://mizage.com/divvy/) for better window management.
- [Encrypto](https://macpaw.com/encrypto) for securing files.
- [ExpressVPN](https://www.expressvpn.com/) for privacy.
- [HyperDock](https://bahoom.com/hyperdock/)
- [Karabiner](https://pqrs.org/osx/karabiner/) for keyboard mapping.
- [Renamer](https://renamer.com/) for easy file renaming.

Miscellaneous

- [Gifox](https://gifox.io/) for GIF making.
- [Rocket](http://matthewpalmer.net/rocket/) for Slack-like emojis.
- [Spotify](https://www.spotify.com/) for music.
- [VLC](http://www.videolan.org/) for a better media player.

Browsers

- [Blisk](https://blisk.io/) for cross-device web development.
- [Brave](https://brave.com/) for web browsing without ads.
- [Chrome](https://www.google.com/chrome/browser/desktop/) for fast and free web browsing.
- [Firefox](https://www.mozilla.org/en-US/firefox/new/) for web browsing and testing.
- [TorBrowser](https://www.torproject.org/projects/torbrowser.html.en) for super secret web browsing.

See `[swag](https://github.com/minamarkham/formation/blob/master/swag)` for the full list of apps that will be installed. Adjust it to your personal taste.

It should take less than 20 minutes to install (depends on your machine).

## Just add `~/.hot-sauce`

![minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/1f336.png](minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/1f336.png)

![minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/hot-sauce.gif](minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/hot-sauce.gif)

Your `~/.hot-sauce` is added at the end of the Formation script. Put your customizations there. For example:

```
#!/usr/bin/env bash

SETUP_ROOT=$HOME/.setup

NERDFONTS_RELEASE=$(curl -L -s -H 'Accept: application/json' https://github.com/ryanoasis/nerd-fonts/releases/latest)
NERDFONTS_VERSION=$(get_github_version $NERDFONTS_RELEASE)

DIRECTORIES=(
 $HOME/Desktop/code
 $HOME/Desktop/design
 $HOME/Desktop/*dump
 $HOME/Desktop/GIFs
 $HOME/Desktop/projects
 $HOME/Desktop/screenshots
)

NERDFONTS=(
 SpaceMono
 Hack
 AnonymousPro
 Inconsolata
)

step "Making directories…"
for dir in ${DIRECTORIES[@]}; do
 mkd $dir
done

step "Installing fonts…"
for font in ${NERDFONTS[@]}; do
 if [ ! -d ~/Library/Fonts/$font ]; then
 printf "${indent} [↓] $font "
 wget -P ~/Library/Fonts https://github.com/ryanoasis/nerd-fonts/releases/download/$NERDFONTS_VERSION/$font.zip --quiet;unzip -q ~/Library/Fonts/$font -d ~/Library/Fonts/$font
 print_in_green "${bold}✓ done!${normal}\n"
 else
 print_muted "${indent}✓ $font already installed. Skipped."
 fi
done
```

Write your customizations such that they can be run safely more than once. See the `slay` script for examples.

Formation functions such as `step` and `link` can be used in your `~/.hot-sauce`.

## Known Issues

Cask does not recognize applications installed outside of Homebrew Cask – in the case that the script fails, you can either remove the application from the install list or uninstall the application causing the failure and try again.

## Acknowledgements

Inspiration and code was taken from many sources, including:

- [Mathias Bynens'](https://github.com/mathiasbynens) [dotfiles](https://github.com/mathiasbynens/dotfiles)
- thoughtbot's [laptop](https://github.com/thoughtbot/laptop/)

## License

![minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/1f4dc.png](minamarkham%20formation%20%F0%9F%92%BB%20macOS%20setup%20script%20for%20fro%2041d86bf386ea4ad18e41f731f91d1aaf/1f4dc.png)

Formation is customized for my own needs. It is free software, and may be redistributed under the terms specified in the [LICENSE](https://github.com/minamarkham/formation/blob/master/LICENSE) file.