---
layout: default
---

# syncthing

```shell
brew install syncthing
```

## Start on boot

Create a new system LaunchDaemon plist file using `sudo`:

```shell
sudo vi /Library/LaunchDaemons/com.syncthing.syncthing.plist
```

Paste the following configuration into the file, replacing `YOUR_USERNAME` with your output from `whoami` and `/opt/homebrew/bin/syncthing` with your output from `which syncthing`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.syncthing.syncthing</string>
    <key>UserName</key>
    <string>YOUR_USERNAME</string>
    <key>ProgramArguments</key>
    <array>
        <string>/opt/homebrew/bin/syncthing</string>
        <string>-no-browser</string>
        <string>-no-restart</string>
        <string>-home=/Users/YOUR_USERNAME/.config/syncthing</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>KeepAlive</key>
    <true/>
    <key>StandardOutPath</key>
    <string>/var/log/syncthing.log</string>
    <key>StandardErrorPath</key>
    <string>/var/log/syncthing-err.log</string>
</dict>
</plist>
```

Ensure standard system file permissions on the plist file:

```shell
sudo chown root:wheel /Library/LaunchDaemons/com.syncthing.syncthing.plist
sudo chmod 644 /Library/LaunchDaemons/com.syncthing.syncthing.plist
```

Load and enable the daemon:

```shell
sudo launchctl load -w /Library/LaunchDaemons/com.syncthing.syncthing.plist
```
