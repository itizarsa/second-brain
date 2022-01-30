# My New Mac Setup (2018-2020)

Source: Notes
Status: Unprocessed
URL: https://www.swyx.io/my-new-mac-setup-4ibi/

![https://www.swyx.io/swyx-ski.jpeg](https://www.swyx.io/swyx-ski.jpeg)

---

![swyx-ski.jpeg](My%20New%20Mac%20Setup%20(2018-2020)%20314909d764b94813ba029bf11e49fd20/swyx-ski.jpeg)

> I have updated my list for 2021 here.
> 

I set up a new Mac for work today. Here's what I did immediately:

- 
    
    Browser: Download Chrome, set to default.
    
- 
    
    Log in to:
    
    - Twitter
    - Github (more setup instructions below)
    - Gmail
- 
    
    Settings:
    
    - Disable Spotlight search for all miscellaneous crap except apps and system preferences
    - Disable Ask Siri
    - Trackpad -> Scroll & Zoom - Natural off
    - Trackpad -> Point & Click -> Look up & data detectors off
    - turn on Airdrop
    - (if using windows keyboard) remap alt and cmd [https://superuser.com/questions/158561/how-can-i-remap-windows-and-alt-keys-in-os-x](https://superuser.com/questions/158561/how-can-i-remap-windows-and-alt-keys-in-os-x)
- 
    
    Finder:
    
    - show filename extensions
    - show dotfiles (just hold Cmd + Shift + . (dot) in a Finder window)
- 
    
    Keyboard:
    
    - copy picture of selected area to clipboard -> Cmd+E
- 
    
    Dock:
    
    - Remove everything from the Dock except: Finder, System Preferences and Trash
    - Turn Hiding on
- 
    
    Chrome extensions:
    
    - Morpheus Dark theme
    - 1password
    - [async render toolbox](https://github.com/sw-yx/async-render-toolbox) (i made this)
- 
    
    Terminal environments
    
    - My dotfiles (vimrc, zshrc, .gitignore_global): [https://gist.github.com/sw-yx/7fa1009e460ecb818d5e6d9ca4616a05](https://gist.github.com/sw-yx/7fa1009e460ecb818d5e6d9ca4616a05)
    - [ZSH](https://ohmyz.sh/) (first usage of `git` will prompt you to install git - takes 15 minutes)
        - `git config --global user.name "swyx"`
        - `git config --global user.email shawnthe1@gmail.com`
            - [syntax highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
                - may need to [chmod stuff](https://stackoverflow.com/questions/13762280/zsh-compinit-insecure-directories) or warnings show at start of every session
                    
                    ```
                    $ sudo chmod -R 755 /usr/local/share/zsh
                    $ sudo chown -R root:staff /usr/local/share/zsh
                    
                    ```
                    
    - [Hyper Terminal](https://hyper.is/)
        - settings: `fontFamily: '"Inconsolata for Powerline", Menlo, "DejaVu Sans Mono", Consolas, "Lucida Console", monospace',`
        - [Fig](https://fig.io/) - context-aware autocomplete for terminal. Waitlisted now, but my version is [here](https://waitlist.withfig.com/download/691b465b-afb9-4776-b179-cc4d78e21345)
            - More CLI tools recommended by Brendan Faik (founder of Fig) - `bat`, `exa`, `ripgrep`, and other [Rust CLI alternatives](https://zaiste.net/posts/shell-commands-rust/). Also [zsh abbreviations](https://github.com/momo-lab/zsh-abbrev-alias)
    - [Homebrew](https://brew.sh/) - i have a bunch more stuff in `brew list` but i'm not sure what i use actively. You can mass install these: `brew install $(cat packages.txt)` bat gdbm libuv [python@3.9](mailto:python@3.9) brotli gh libyaml readline c-ares go mpdecimal ruby deno gradle nghttp2 sqlite diff-so-fancy icu4c node xz fnm jemalloc openjdk yarn fzf libev [openssl@1.1](mailto:openssl@1.1) z
        
        ```
         ```
        
        ```
        

```
      - `brew install bat`
      - [Github CLI](https://github.com/cli/cli): `brew install github/gh/gh`
        - you need to login to git - if you have 2fa enabled, you cant use your normal github password. try pushing to a repo and enter in a [Personal Access Token](https://stackoverflow.com/a/34919582) for password.
        - then run `gh auth login`
        - [add GitHub SSH key](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) (not optional)
      - `brew install [fzf](https://github.com/junegunn/fzf)` - usage example is [here](https://twitter.com/swyx/status/1048009961723318272)
      - [yarn](https://yarnpkg.com/en/docs/install#mac-stable) note `brew install yarn --ignore-dependencies` since i use nvm
         - you may need to [work around Mac OS Sierra](https://stackoverflow.com/questions/43780207/installing-node-with-brew-fails-on-mac-os-sierra) and install node first
      - [`brew install z`](https://brewinstall.org/install-z-on-mac-with-brew/) - REALLY GOOD TRY IT
      - `brew install python`
      - `brew install ruby`
      - `brew install deno`
      - `brew install gradle`
      - `pip3 install --user powerline-status`
      - go to a neutral folder and `git clone https://github.com/powerline/fonts && cd fonts && ./install.sh`
  - `brew install node` [Node.js/NPM](https://nodejs.org/en/download/)
      - `npm login`
      - `sudo npm install netlify-cli -g`
      - `npm i -g sign-bunny fortune-node parrotsay`
      - `npm install -g undollar` for removing $
      - `sudo npm install -g @aws-amplify/cli`
      - `amplify configure`
      - `sudo npm install -g trash-cli`
  - [fnm](https://github.com/Schniz/fnm) faster alternative to [nvm](https://github.com/creationix/nvm): `curl -fsSL https://fnm.vercel.app/install | bash` or `brew install fnm`
  - [Anaconda](https://www.anaconda.com/download/#macos
  - [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac/)
  - `brew install java` - [Java Development Kit](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)
  - `brew install [go](https://golang.org/dl/)` dont forget `export PATH=$PATH:/usr/local/go/bin`
  - `fontFamily: '"Inconsolata for Powerline", Menlo, "DejaVu Sans Mono", Consolas, "Lucida Console", monospace',`
  - `brew install [diff-so-fancy](https://www.npmjs.com/package/diff-so-fancy)` - `git config --global core.pager "diff-so-fancy | less --tabs=4 -RFX"`

You can also diff with this bash function `dif() { git diff --color --no-index "$1" "$2" | diff-so-fancy; }` or with VSCode `code --diff file1.js file2.js`.

You can also try https://github.com/dandavison/delta

- Emojis: https://matthewpalmer.net/rocket/
- Password Manager: https://www.1password.com/ (i have a company account)
- Window Manager: https://www.spectacleapp.com/
    - launch at login
- Clipboard Manager: https://clipy-app.com/
- Loom: https://www.loom.com/desktop
- Screenshots: https://cleanshot.com/ (previously used https://zapier.com/zappy)
- Caffeine (Keep Mac awake for talks): https://intelliscapesolutions.com/apps/caffeine (used to be http://lightheadsw.com/caffeine/)
- Video capture: https://getkap.co/
- Dual Screen: https://www.duetdisplay.com/
- Gifs: [Licecap](https://www.cockos.com/licecap/)
- [Slack](https://slack.com/downloads/osx) or [Discord](https://discord.com/)
- OBS: https://obsproject.com/
- SkyFonts: https://www.fonts.com/web-fonts/google
- Microsoft Todo: https://apps.apple.com/app/apple-store/id1274495053?mt=8
- Stretchly: https://hovancik.net/stretchly/
- SimpleNote: https://apps.apple.com/us/app/simplenote/id692867256?ls=1&mt=12
- [Superhuman for Mac](http://superhuman.com/mac) and https://mail.superhuman.com
- Notion: https://www.notion.so/desktop
   - https://chrome.google.com/webstore/detail/notion-web-clipper/knheggckgoiihginacbkhaalnibhilkk?hl=en
- App Search/Utils: https://www.alfredapp.com/
    - set to Alfred Dark
    - [airdrop to iphone/ipad](https://github.com/swmoon203/CrossShare/blob/master/Alfred%20Workflow/Cross%20Share%20Airdrop.alfredworkflow)
    - [Cupcake Ipsum](http://www.packal.org/workflow/cupcake-ipsum)
- Editor: Download [VS Code](https://code.visualstudio.com/download) (I used to use Insiders but the popups are super annoying). use Settings Sync to sync across machines
  - have to set up powerline fonts "Meslo LG M for Powerline" ([download](https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf))
  - auto-close-tag v0.5.6
  - auto-rename-tag v0.0.15
  - Bookmarks v9.1.0
  - code-settings-sync v3.1.2
  - debugger-for-chrome v4.10.2
  - es7-react-js-snippets v1.8.7
  - graphql-for-vscode v1.12.1
  - mdx v0.1.0
  - prettier-vscode v1.6.1
  - python v2018.9.2
  - python v0.2.3
  - rainbow-brackets v0.0.6
  - shades-of-purple v3.17.0
  - vscode-graphql v0.1.5
  - vscode-import-cost v2.9.0
  - vscode-styled-components v0.0.23
  - vscode-wakatime v1.2.3
  - [TabNine](https://www.tabnine.com/) AI completions
  - [GitHub Copilot](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)

---

## Other good "new laptop setup" lists:

- https://github.com/minamarkham/formation
- [Tania Rascia's setup](https://www.taniarascia.com/setting-up-a-brand-new-mac-for-development/?ck_subscriber_id=591519942)
- [Nick Nisi's dotfiles](https://github.com/nicknisi/dotfiles)
- [Mathias Bynens macos defaults](https://github.com/mathiasbynens/dotfiles/blob/master/.macos)

```