---
layout: default
---

# WSL

These tips are based on using the Ubuntu version of [WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10) which is currently at version 18.04 LTS. Before installing Ubuntu from the Microsoft Store, open Powershell as administrator and run this command

```shell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

Windows drives (usually called C and D) are available in `/mnt` and you can work in these drives from the Linux command line. An important point to remember: **never edit a file under Linux using a Windows program**. The best approach is to save all your work files in C or D drive and never under Linux. For example, you can create directories in D drive and make symlinks from your home directory under Linux

```shell
cd $HOME
mkdir /mnt/d/Work
ln -s /mnt/d/Work Work
mkdir /mnt/d/Tex
ln -s /mnt/d/Tex Tex
```

In addition, you can create symlinks to some useful Windows folders (replace USERNAME with your Windows user name)

```shell
cd $HOME
ln -s /mnt/c/Users/USERNAME/Desktop   Desktop
ln -s /mnt/c/Users/USERNAME/Documents Documents
ln -s /mnt/c/Users/USERNAME/Downloads Downloads
```

In Ubuntu, we install some important programs using apt

```shell
sudo apt install gcc gfortran
sudo apt install python                (required by spack)
sudo apt install python3-numpy
sudo apt install python3-scipy
sudo apt install python3-sympy
sudo apt install python3-matplotlib
sudo apt install jupyter
sudo apt install gnuplot               (install xming)
sudo apt install gv
sudo apt install xpdf
```

and the rest we install using [Spack](comp/spack.html). Other applications can be installed on Windows side, e.g., FileZilla, FireFox, gVim, VisIt, VLC, gmsh, SourceTree, MikTex and VS Code. We can run these Windows programs from the Linux command line by defining some aliases, see sample bashrc file [here](https://github.com/cpraveen/cfdlab/blob/master/bin/bashrc_wsl.txt) which you can add at the end of your `$HOME/.bashrc` file.

## Miscellaneous

<ul>

<li>
Search: press Windows Key and type your query.
</li>

<li>
Lock screen: press Ctrl+Alt+Delete and select Lock, or press Windows key + L key.
</li>

<li>
Disable Windows bell sound, etc. in bash: Open <code>$HOME/.inputrc</code> and add the lines

<pre>
set bell-style none
set completion-ignore-case on
set show-all-if-ambiguous on
</pre>
</li>

<li>
To set gvim font, add following line to file <code>/mnt/c/Users/USERNAME/.gvimrc</code>

<pre>
set guifont=Consolas:h11
</pre>
</li>

<li>OpenMPI would give some warning message at end of each run; do this to get rid of this message

<pre>
echo 0 | sudo tee /proc/sys/kernel/yama/ptrace_scope
</pre>
</li>

</ul>
