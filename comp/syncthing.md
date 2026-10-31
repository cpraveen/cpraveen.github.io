---
layout: default
---

# syncthing

```shell
brew install syncthing
```

## Start on boot

Do this if you want syncthing to start without having to login in. It is useful on headless servers. This will start the syncthing daemon when your computer boots.

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

See the web interface

```shell
open http://127.0.0.1:8384
```

## Sharing device and folder

See device id

```shell
syncthing cli show system | jq .myID
```

Share device on both local and remote

```shell
# On remote
syncthing cli config devices add --device-id $LocalID
# On local
syncthing cli config devices add --device-id $RemoteID
```

Add a folder on local

```shell
FolderID=`dd if=/dev/urandom count=1024 2> /dev/null | sha1sum --quiet`
syncthing cli config folders add --label LABEL --path FOLDER --id $FolderID 
```

Share folder to remote

```shell
syncthing cli config folders $FolderID devices add --device-id $RemoteID
```

On remote, check pending invitation

```shell
syncthing cli show pending folders
```

On remote, add folder and share it back

```shell
syncthing cli config folders add --id $FolderID --label LABEL --path FOLDER
syncthing cli config folders $FolderID devices add --device-id $LocalID
```
