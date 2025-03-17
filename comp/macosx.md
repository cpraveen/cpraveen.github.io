---
layout: default
---

# Computing on Mac OSX

Mac OSX comes with a huge collection of free tools pre-installed and has almost everything that a developer needs for C/C++ coding. Other things need to be installed. I mainly used two package managers for this.

1. [Homebrew](comp/brew.html)
1. [Spack](comp/spack.html)

## Command line tools

This gives you compilers, git, etc.; you can install it by

```shell
sudo xcode-select --install
```

Sometimes, I find it necessary to delete the existing command line tools and then install to get the latest version

```shell
sudo rm -rf /Library/Developer/CommandLineTools
sudo xcode-select --install
```

## Searching your desktop

<a href="https://www.alfredapp.com">Alfred</a> is so much better than Spotlight, it is now my preferred tool for searching my mac. It uses the Spotlight index to perform the search, so you need to have Spotlight enabled. In Alfred preferences, specify locations where it should search, e.g.,

```shell
~
/Applications
/Volumes/Samsung_T5
```

If Spotlight is not indexing external usb drives

```shell
rm -rf /Volumes/Samsung_T5/.Spotlight-V100
sudo mdutil -E /Volumes/Samsung_T5
```

If search is not finding files, then rebuild Spotlight index

```shell
sudo mdutil -a -i off
sudo mdutil -X /System/Volumes/Data  # First try without this step and see if it fixes
sudo mdutil -a -i on
sudo mdutil -E
```

## Text editors

For coding, you can use the editor in XCode but XCode is a big package and I prefer not to install it. Instead I use [VSCode](https://code.visualstudio.com)  which is free and can be installed from Homebrew. You can use the Vim plugin in VSCode if you are a Vim user.  Another option is <a href="https://macvim-dev.github.io/macvim/">MacVim</a> with [NerdTree](https://github.com/preservim/nerdtree) for file browsing.

## Diff tool

OSX comes with a nice diff tool called opendiff which can be invoked from the command line to compare two files side by side, but this needs XCode. Other options are VSCode,

```shell
code -n -d file1 file2
```

or, meld and tkdiff (install via homebrew).

## Version control

git is already available and I use <a href="https://www.sourcetreeapp.com">SourceTree</a> as a gui for git.

## Python

You can install Python using brew but I use <a href="https://github.com/conda-forge/miniforge">miniforge</a> to get a Python installation.

```shell
brew install miniforge
conda install ...
```

## Plotting/visualization tools

<a href="http://www.gnuplot.info">Gnuplot</a> is really useful to do some quick and simple visualizations. Install via brew

```shell
brew install gnuplot
```

To generate line plots for publication, <a href="https://matplotlib.org">Matplotlib</a> is probably the most useful. Install this from your Python distribution.

<a href="https://wci.llnl.gov/simulation/computer-codes/visit/executables">VisIt</a> is my favourite program for visualizing PDE solutions coming from finite difference/volume/element methods. You may also want to try <a href="https://www.paraview.org">Paraview</a> which is also very powerful tool.

## Document preparation/viewing

<a href="https://www.tug.org/mactex/">MacTex</a> is a nice way to install all the Latex packages.

<a href="https://www.texstudio.org/">TexStudio</a> is a great editor for Latex.

To manage my bibliography, I have come to like <a href="https://www.zotero.org">Zotero</a> a lot.

<a href="http://texmacs.org/">TexMacs</a> is a wysiwyg editor that seems to be getting very good. I sometimes use it for writing small notes and documents.

The built in Preview app can open and display many file types including pdf. [Skim](https://skim-app.sourceforge.io/) is another good alternative, which I prefer for making pdf presentations, as it is better than Preview. Skim can also open ps/eps files.

<a href="http://djvu.sourceforge.net">djview</a>: For viewing djvu archive files. Most ebooks are packaged as djvu files. The available binaries are old versions; you can install this via brew (<code>brew install djview</code>).

Keynote is free with OSX and is surprisingly good, even better than PowerPoint. You also get Pages for free which is an alternative to Word.

<a href="https://www.libreoffice.org">LibreOffice</a>: Built on openoffice.

## File transfer

<a href="https://filezilla-project.org">FileZilla</a> lets you setup some servers so that you can quickly transfer files between your computers.

## Image tools

<a href="http://asymptote.sourceforge.net">Asymptote</a>: Asymptote is a powerful descriptive vector graphics language that provides a natural coordinate-based framework for technical drawing. Labels and equations are typeset with LaTeX, for high-quality PostScript output. If you installed MaxTex, then you already have asymptote. Otherwise you can install it using brew.

<a href="https://www.imagemagick.org/script/index.php">ImageMagick</a>: Use ImageMagick to create, edit, compose, or convert bitmap images. It can read and write images in a variety of formats (over 200) including PNG, JPEG, GIF, HEIC, TIFF, DPX, EXR, WebP, Postscript, PDF, and SVG. Use ImageMagick to resize, flip, mirror, rotate, distort, shear and transform images, adjust image colors, apply various special effects, or draw text, lines, polygons, ellipses and Bezier curves.

<a href="http://markummitchell.github.io/engauge-digitizer/">Engauge</a>: This open source, digitizing software converts an image file showing a graph or map, into numbers. The image file can come from a scanner, digital camera or screenshot. The numbers can be read on the screen, and written or copied to a spreadsheet

<a href="https://inkscape.org">Inkscape</a>: Inkscape is a Vector Graphics Editor, similar to Adobe Illustrator, that strives to be SVG Compliant, open source, responsive and extensible.

## Video player

While I have experimented many, <a href="https://lhc70000.github.io/iina/">IINA</a> is the one I now use.

## Browser

Safari works well; other options are <a href="https://www.mozilla.org/en-US/firefox/new/">Firefox</a> and <a href="https://www.opera.com">Opera</a>.  (Avoid Chrome like the plague)

## Some command line stuff

```shell
softwareupdate -l
```

E.g., to update CLT, find the latest available version with above command and copy the `Label`

```shell
softwareupdate -i "<Label>" --verbose
```

## Creating bootable USB drive on MacOS

Convert iso file to dmg

```shell
hdiutil convert -format UDRW -o foo foo.iso
```

This creates `foo.dmg` file. List the drives and find drive `/dev/diskN` associated to the USB device

```shell
diskutil list
```

Unmount it

```shell
diskutil unmountDisk /dev/diskN
```

Copy the dmg file

```shell
sudo dd if=foo.dmg of=/dev/rdiskN bs=1m
```

When it finishes, you can remove the USB drive.

## Miscellaneous stuff

<ol>

<li>
If you are behind a proxy server, then to get server settings to be visible under sudo, you need to set some environment variables for http and rsync and do the following

<pre>
sudo visudo
</pre>

Enter your password and add the following additional lines and save the file. You need to know how to use vi/vim for this.

<pre>
Defaults env_keep += "http_proxy HTTP_PROXY"
Defaults env_keep += "https_proxy HTTPS_PROXY"
Defaults env_keep += "ftp_proxy FTP_PROXY"
Defaults env_keep += "rsync_proxy RSYNC_PROXY"
</pre>
</li>

<li>
<a href="https://freemacsoft.net/appcleaner/">AppCleaner</a> allows you to uninstall apps and all associated files.
</li>

<li>
To see some info on your wireless connection, click Option + wifi icon in menubar.
</li>

<li>
Use pmset to manage power usage, sleep, etc.  You can check the settings by (do this check while using charger and then on battery)

<pre>
pmset -g
</pre>

You can see my settings <a href="https://github.com/cpraveen/cfdlab/blob/master/bin/pmset.sh">here</a>.
</li>

<li>
Reset NVRAM from terminal

<pre>
sudo nvram -c
sudo reboot
</pre>
</li>

<li>
To disable laptop auto booting on lid opening/power adaptor connection

<pre>
sudo nvram BootPreference=%00 # Redo this if NVRAM is reset
</pre>

To reenable auto boot

<pre>
sudo nvram -d BootPreference
</pre>
</li>

<li>
Sometimes Activity Monitor does not display any columns. Then delete the preferences file

<pre>
rm ~/Library/Preferences/com.apple.ActivityMonitor.plist
</pre>

and reopen it.
</li>

<li>
Reset icons in launchpad

<pre>
defaults write com.apple.dock ResetLaunchPad -bool true && killall Dock
</pre>
</li>

<li>
Reset Finder views/settings

<pre>
cd ~
find . -name ".DS_Store" -delete
rm ~/Library/Preferences/com.apple.finder.plist
</pre>
</li>

<li>
Enable repeat key press, useful for Vim mode in VSCode, overleaf, etc.

<pre>
defaults write NSGlobalDomain ApplePressAndHoldEnabled -bool false
</pre>
</li>

<li>
Get expanded desktop view in mission control using <a href="https://github.com/briankendall/forceFullDesktopBar">this</a>, needs SIP to be disabled.
</li>

<li>
Disable Safari tab preview

<pre>
defaults write com.apple.Safari DebugDisableTabHoverPreview 1
</pre>
</li>

<li>
Disable spelling correction, etc.: System Preferences --> Keyboard --> Text
</li>

<li>
Getting display of X11 programs running on remote Mac: On your remote Mac, add following to <code>/etc/ssh/sshd_config</code>

<pre>
X11Forwarding yes
X11DisplayOffset 10
X11UseLocalhost yes
XauthLocation /opt/X11/bin/xauth
</pre>

and restart ssh service

<pre>
sudo launchctl unload /System/Library/LaunchDaemons/ssh.plist
sudo launchctl load -w /System/Library/LaunchDaemons/ssh.plist
</pre>

</li>

</ol>
