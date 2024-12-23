---
layout: default
---

# TeXMacs

## User preferences

Your settings are saved in `$HOME/.TeXmacs` directory. Sometimes this may get corrupted and lead to weird issues; just delete this directory an restart TeXmacs. You will of course lose your settings, so you need to add them back.

## Python

Set python path in `/Applications/TeXmacs.app/Contents/Resources/share/TeXmacs/plugins/python/progs`

```text
(define (python-command) "/opt/homebrew/Caskroom/miniforge/base/bin/python")
```

## PDF output

Set PDF version in `Edit -> Preferences -> Convert -> Pdf -> Pdf version number`. This setting is saved in `$HOME/.TeXmacs/system/preferences.scm` file.
