---
layout: default
---

# Vim tips and tricks

Vim is a very powerful text editor designed for productivity. You can also using gui versions like [gvim](http://www.vim.org/download.php) or [MacVim](https://github.com/macvim-dev/macvim).

## vimrc

Below I have listed some settings in vim which make your editing life easier.

<ul>

<li>
Disabling file backups: Vim makes backups of files which are edited. Disable this with

<pre>
set nobackup
</pre>
</li>

<li>
Disable displaying line numbers with

<pre>
set nonumber
</pre>

</li>

<li>
If you enable the showmatch option, then whenever you start and close a bracket, then it automatically shows the matching brackets. This is useful for some programming languages like C.

<pre>
set showmatch
</pre>

</li>

<li>
You can set the number of spaces for each tab

<pre>
set tabstop=6
</pre>

</li>

<li>
Some languages like fortran 77 require seven blank spaces at the beginning of each line. You can set tabstop to seven and convert the tab into ordinary spaces by((Sometimes you may need a tab, like in a makefile))

<pre>
set expandtab
</pre>

</li>

<li>
Indenting of a code makes it easier to read it. Set auto indenting with

<pre>
set ai
</pre>

</li>

<li>
When you are typing a text document like in LaTex, long lines may not properly flow to next line and a word can appear on two lines. Use the following setting to shift to new line without putting a new line character

<pre>
set linebreak
</pre>

</li>

<li>
If you would rather put a new line character at the end of each physical line, use

<pre>
set wrap wrapmargin=4
</pre>

</li>

<li>
When you have a line that spans more than one physical line, then the cursor simple jumps to the next line. You can make the cursor move by one physical line each time with

<pre>
nmap  j gj
nmap  k gk
</pre>

</li>

<li>
While editing a paragraph, its formatting can get spoiled because you may make some changes in the middle of the paragraph. Then define the following key binding and use it whenever you want to reformat a paragraph

<pre>
nmap gqap <F8>
</pre>

</li>

</ul>

## Comment selected lines

Visually select the lines you want to comment using SHIFT + v. Then press semi-colon ":" which will give you

```
:'<,'>
```

Then type

```
:'<,'> s/^/#
```

## Getting file browser

If you are editing some code which is in multiple files, it is useful to have a file browser. The plugin <a href="https://github.com/scrooloose/nerdtree">NERDTree</a> provides such a file browser. After starting vim, gvim or macvim, type

```
:NERDTree
```

to get the file browser. You can double click a file to open it.

## Setting up

Install [pathogen](https://github.com/tpope/vim-pathogen)

Install bundles you want, e.g., to install NERDTree

```shell
git clone https://github.com/preservim/nerdtree.git ~/.vim/bundle/nerdtree
```

## Links

1. [Best of VIM tips](http://rayninfo.co.uk/vimtips.html)
