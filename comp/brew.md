---
layout: default
---

# Homebrew

[Homebrew](https://brew.sh) is the best package manager for Mac. Nowadays, I have switched to [Spack](comp/spack.html) for installing scientific software since brew does not have all the things that I need. I only install a few packages from brew, see below.

You need to install command line tools before installing packages with homebrew. Note that you do not need to install XCode. Apple's Command Line Tools can be installed on recent OS versions by running this command in the Terminal

```shell
xcode-select --install
```

Run doctor and config to check that your setup is ok before installing any packages

```shell
brew doctor
brew config
```

Sometimes I have found it necessary to delete existing tools and then install to get the latest version

```shell
sudo rm -rf /Library/Developer/CommandLineTools
xcode-select --install
```

Here are some useful commands.

```text
brew install gcc          -- Install some package, e.g., gcc
brew uninstall gcc        -- Uninstall a package
brew info gcc             -- Check package information
brew list                 -- List all installed packages
brew list gcc             -- Show files installed by gcc
brew list --verbose gcc   -- Same as above but more detailed
brew update               -- Update package list (needs internet connection)
brew outdated             -- See outdated packages
brew upgrade              -- Upgrade all outdated packages
brew upgrade -n           -- Do dry run of upgrade
brew upgrade gcc          -- Upgrade a specific package
brew cleanup              -- Remove old versions of packages
brew cleanup --prune=all  -- Remove all downloads
brew deps gcc             -- Check dependencies for gcc
brew uses --installed gcc -- Check which installed packages depend on gcc
brew leaves               -- List packages not required by any installed package
```

We will only install some basic packages from Homebrew and the rest of the scientific softwares using [Spack](comp/spack.html).

```shell
brew install aspell
brew install astyle
brew install chapel
brew install colordiff
brew install diffr
brew install dos2unix
brew install enscript
brew install ffmpeg
brew install gcc
brew install gnuplot
brew install imagemagick
brew install ispell
brew install subversion
brew install wget
brew install youtube-dl
```

Install specific version of gcc that you need

```shell
brew install gcc@9
```

Pin a package to prevent it from being upgraded

```shell
brew pin gcc@11
```

You can see pinned packages

```shell
brew list --pinned
```

Uninstall formulae that were only installed as a dependency of another formula
and are now no longer needed

```shell
brew autoremove
```

To reinstall all installed formulae, e.g., after a major OS upgrade

```shell
brew list --formula | xargs brew reinstall
```

## Binary apps

All of these are installed into the `/Applications` directory.

```shell
brew install alfred
brew install amazon-music
brew install appcleaner
brew install coconutbattery
brew install djview
brew install dropbox
brew install firefox
brew install google-drive
brew install iina
brew install inkscape
brew install keepassxc
brew install lastpass
brew install lyx
brew install mactex
brew install meld
brew install onyx
brew install paraview
brew install sourcetree
brew install skype
brew install texmacs
brew install texstudio
brew install visit
brew install visual-studio-code
brew install xquartz
brew install yed
brew install zoom
brew install zotero
```

Some apps are available as both bottles and casks, and I prefer to install cask versions and they install into `/Applications` folder.

```shell
brew install --cask docker
brew install --cask julia
brew install --cask macvim
brew install --cask miniforge     # installs conda python
```

To install Octave

```shell
brew tap octave-app/octave-app
brew install --cask octave-app
```
