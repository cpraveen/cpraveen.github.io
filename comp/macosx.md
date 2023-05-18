---
layout: default
---

# Computing on Mac OSX

Mac OSX comes with a huge collection of free tools pre-installed and has almost everything that a developer needs for C/C++ coding. Other things need to be installed. I mainly used two package managers for this.

1. [Homebrew](comp/brew.html)
1. [Spack](comp/spack.html)

## Searching your desktop

<a href="https://www.alfredapp.com">Alfred</a> is so much better than Spotlight, it is now my preferred tool for searching my mac. It uses the Spotlight index to perform the search, so you need to have Spotlight enabled.

## Text editors

For C/C++ coding, I prefer VSCode which is free and can be installed from Homebrew. Also make sure command line tools are installed, you can install it by

```shell
sudo xcode-select --install
```

Sometimes, I find it necessary to delete the existing command line tools and then install the latest version

```shell
sudo rm -rf /Library/Developer/CommandLineTools
sudo xcode-select --install
```

<a href="https://code.visualstudio.com">VS Code</a> is also an excellent code editor and I use this for Fortran and Python. For Python and Fortran coding, another option is <a href="https://macvim-dev.github.io/macvim/">MacVim</a> with NerdTree for file browsing.

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

<a href="http://get.adobe.com/reader/otherversions/">Acrobat</a>: For viewing pdf files, but I find this a very heavy application and avoid using it normally. I prefer to use builtin Preview. But there are some times when your PDF doesnt display properly and you absolutely need this. Keep it installed for those times.

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
On new versions like Catalina, the battery discharges overnight even if the laptop is in sleep because it is waking up for network. In System Preferences --> Energy Saver --> Battery, disable "Enable Power Nap while on battery power". To disable network while sleeping on battery

<pre>
sudo pmset -b tcpkeepalive  0    # Redo if you did SMC/NVRAM reset or os update
sudo pmset -a hibernatemode 25
sudo pmset -a standby       1
</pre>

You can check the settings by (do this check while using battery)

<pre>
pmset -g
</pre>

Use only integrated GPU when on battery

<pre>
sudo pmset -b gpuswitch 0
</pre>

Here are the various power states

<pre>
-a - global (same behavior for charging and battery states)
-c - charging
-b - battery
</pre>

Here are the possible options for gpuswitch

<pre>
0 - integrated GPU only
1 - discrete GPU only
2 - autoswitch GPU
</pre>
</li>

<li>
To disable laptop auto booting on lid opening

<pre>
sudo nvram AutoBoot=%00 # Redo if NVRAM is reset
</pre>

To reenable auto boot

<pre>
sudo nvram AutoBoot=%03
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
PulseSecure starts automatically on login. Disable it like this

<pre>
sudo rm /Library/LaunchAgents/net.pulsesecure.pulsetray.plist
</pre>

Then, add symlink to `/Applications`

<pre>
sudo ln -s /Applications/Pulse\ Secure.app/Contents/Plugins/JamUI/PulseTray.app \
           /Applications/PulseTray.app
</pre>

and use PulseTray to launch PulseSecure in future.
</li>

<li>
Reset NVRAM from terminal

<pre>
sudo nvram -c
sudo shutdown -r now
</pre>
</li>

<li>
Reset icons in launchpad

<pre>
defaults write com.apple.dock ResetLaunchPad -bool true && killall Dock
</pre>
</li>

<li>
BigSur messed up the menu bar design in app windows, to get previous type view do this

<pre>
defaults write -g NSWindowSupportsAutomaticInlineTitle -bool false
</pre>

You have to quit and start the app for this to take effect. (Does not seem to work in Monterey)
</li>

<li>
Reset Finder views/settings

<pre>
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

</ol>
