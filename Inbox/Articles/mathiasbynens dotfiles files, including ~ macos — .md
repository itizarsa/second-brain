# mathiasbynens/dotfiles: .files, including ~/.macos — sensible hacker defaults for macOS

Source: Notes
Status: Unprocessed
URL: https://github.com/mathiasbynens/dotfiles

[https://opengraph.githubassets.com/d312fc674cad52953a52b0854ab74a3cf71703e046b6bc7c43c5c00cf4d8bce4/mathiasbynens/dotfiles](https://opengraph.githubassets.com/d312fc674cad52953a52b0854ab74a3cf71703e046b6bc7c43c5c00cf4d8bce4/mathiasbynens/dotfiles)

---

# Mathias’s dotfiles

[mathiasbynens%20dotfiles%20files,%20including%20~%20macos%20%E2%80%94%20%20dc62b604f7964180a08854c896ffb73d/68747470733a2f2f692e696d6775722e636f6d2f456b45747068432e706e67](mathiasbynens%20dotfiles%20files,%20including%20~%20macos%20%E2%80%94%20%20dc62b604f7964180a08854c896ffb73d/68747470733a2f2f692e696d6775722e636f6d2f456b45747068432e706e67)

## Installation

**Warning:** If you want to give these dotfiles a try, you should first fork this repository, review the code, and remove things you don’t want or need. Don’t blindly use my settings unless you know what that entails. Use at your own risk!

### Using Git and the bootstrap script

You can clone the repository wherever you want. (I like to keep it in `~/Projects/dotfiles`, with `~/dotfiles` as a symlink.) The bootstrapper script will pull in the latest version and copy the files to your home folder.

```
git clone https://github.com/mathiasbynens/dotfiles.git && cd dotfiles && source bootstrap.sh
```

To update, `cd` into your local `dotfiles` repository and then:

```
source bootstrap.sh
```

Alternatively, to update while avoiding the confirmation prompt:

```
set -- -f; source bootstrap.sh
```

### Git-free install

To install these dotfiles without Git:

```
cd; curl -#L https://github.com/mathiasbynens/dotfiles/tarball/main | tar -xzv --strip-components 1 --exclude={README.md,bootstrap.sh,.osx,LICENSE-MIT.txt}
```

To update later on, just run that command again.

### Specify the `$PATH`

If `~/.path` exists, it will be sourced along with the other files, before any feature testing (such as [detecting which version of `ls` is being used](https://github.com/mathiasbynens/dotfiles/blob/aff769fd75225d8f2e481185a71d5e05b76002dc/.aliases#L21-L26)) takes place.

Here’s an example `~/.path` file that adds `/usr/local/bin` to the `$PATH`:

```
export PATH="/usr/local/bin:$PATH"
```

### Add custom commands without creating a new fork

If `~/.extra` exists, it will be sourced along with the other files. You can use this to add a few custom commands without the need to fork this entire repository, or to add commands you don’t want to commit to a public repository.

My `~/.extra` looks something like this:

```
# Git credentials
# Not in the repository, to prevent people from accidentally committing under my name
GIT_AUTHOR_NAME="Mathias Bynens"
GIT_COMMITTER_NAME="$GIT_AUTHOR_NAME"
git config --global user.name "$GIT_AUTHOR_NAME"
GIT_AUTHOR_EMAIL="mathias@mailinator.com"
GIT_COMMITTER_EMAIL="$GIT_AUTHOR_EMAIL"
git config --global user.email "$GIT_AUTHOR_EMAIL"
```

You could also use `~/.extra` to override settings, functions and aliases from my dotfiles repository. It’s probably better to [fork this repository](https://github.com/mathiasbynens/dotfiles/fork) instead, though.

### Sensible macOS defaults

When setting up a new Mac, you may want to set some sensible macOS defaults:

```
./.macos
```

### Install Homebrew formulae

When setting up a new Mac, you may want to install some common [Homebrew](https://brew.sh/) formulae (after installing Homebrew, of course):

```
./brew.sh
```

Some of the functionality of these dotfiles depends on formulae installed by `brew.sh`. If you don’t plan to run `brew.sh`, you should look carefully through the script and manually install any particularly important ones. A good example is Bash/Git completion: the dotfiles use a special version from Homebrew.

## Feedback

Suggestions/improvements [welcome](https://github.com/mathiasbynens/dotfiles/issues)!

## Author

[mathiasbynens%20dotfiles%20files,%20including%20~%20macos%20%E2%80%94%20%20dc62b604f7964180a08854c896ffb73d/687474703a2f2f67726176617461722e636f6d2f6176617461722f32346530386139656138346465623137616531323130373464306631373132353f733d3730](mathiasbynens%20dotfiles%20files,%20including%20~%20macos%20%E2%80%94%20%20dc62b604f7964180a08854c896ffb73d/687474703a2f2f67726176617461722e636f6d2f6176617461722f32346530386139656138346465623137616531323130373464306631373132353f733d3730)

---

[Mathias Bynens](https://mathiasbynens.be/)

---

## Thanks to…

- @ptb and [his *macOS Setup* repository](https://github.com/ptb/mac-setup)
- [Ben Alman](http://benalman.com/) and his [dotfiles repository](https://github.com/cowboy/dotfiles)
- [Cătălin Mariș](https://github.com/alrra) and his [dotfiles repository](https://github.com/alrra/dotfiles)
- [Gianni Chiappetta](https://butt.zone/) for sharing his [amazing collection of dotfiles](https://github.com/gf3/dotfiles)
- [Jan Moesen](http://jan.moesen.nu/) and his [ancient `.bash_profile`](https://gist.github.com/1156154) + [shiny *tilde* repository](https://github.com/janmoesen/tilde)
- Lauri ‘Lri’ Ranta for sharing [loads of hidden preferences](https://web.archive.org/web/20161104144204/http://osxnotes.net/defaults.html)
- [Matijs Brinkhuis](https://matijs.brinkhu.is/) and his [dotfiles repository](https://github.com/matijs/dotfiles)
- [Nicolas Gallagher](http://nicolasgallagher.com/) and his [dotfiles repository](https://github.com/necolas/dotfiles)
- [Sindre Sorhus](https://sindresorhus.com/)
- [Tom Ryder](https://sanctum.geek.nz/) and his [dotfiles repository](https://sanctum.geek.nz/cgit/dotfiles.git/about)
- [Kevin Suttle](http://kevinsuttle.com/) and his [dotfiles repository](https://github.com/kevinSuttle/dotfiles) and [macOS-Defaults project](https://github.com/kevinSuttle/macOS-Defaults), which aims to provide better documentation for `[~/.macos](https://mths.be/macos)`
- [Haralan Dobrev](https://hkdobrev.com/)
- Anyone who [contributed a patch](https://github.com/mathiasbynens/dotfiles/contributors) or [made a helpful suggestion](https://github.com/mathiasbynens/dotfiles/issues)