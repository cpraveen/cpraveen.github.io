---
layout: default
---

# Tips to use ssh effectively

## Workstations at CAM

There are two workstations "euler" and "fourier", see [this page](comp/comp.html). To connect to them from inside CAM, do

```shell
ssh euler
ssh fourier
```

To login from outside CAM, please ask me for details. When you connect from outside CAM, display may not work, you have to do all work from the terminal.

On euler or fourier, check your `$HOME/.bashrc` file. It runs a script in my directory to set some paths to various softwares. You can examine this file using vi/vim

```shell
vi /home/praveen/.setenv
```

Everything you need should be installed already. If something is missing, tell me about it.

## SSH keys

YOU SHOULD SETUP SSH KEYS so you can login without typing password everytime.

On your laptop/desktop, run the following ONCE

```shell
ssh-keygen
```

Then just enter for all questions. This creates a directory `$HOME/.ssh` which contains some files. The file `$HOME/.ssh/id_rsa.pub` is your public key which must be copied to the remote server. You can do this manually by logging into the remote server and copy the contents of `$HOME/.ssh/id_rsa.pub` from your local computer to `$HOME/.ssh/authorized_keys` on the remote computer. Alternately, you can use ssh-copy-id command.

### You are inside cam

From your local computer, do

```shell
ssh-copy-id USERNAME@REMOTEHOST
```

where USERNAME is your username on the REMOTEHOST. Enter password for your REMOTEHOST to copy the ssh id.

### You are outside cam

From your local computer, do

```shell
ssh-copy-id -p PORT USERNAME@158.144.181.10
```

"PORT" depends on which computer you are connecting to, euler, fourier, etc. USERNAME is your username on the remote computer, euler, fourier, etc.

## SSH to github, bitbucket, etc.

Copy the contents of your `$HOME/.ssh/id_rsa.pub` file into your github or bitbucket account by logging in through your browser. This option should be available somewhere in the settings part of your github/bitbucket account. Once keys are setup, you can clone and do push/pull without entering your github/bitbucket password everytime. E.g., clone using git

```shell
git clone git@github.com:USERNAME/PROJECT.git
```

Here USERNAME is your github username and PROJECT is the name of the git repository you want to clone.

## Disable password based login

Edit the file

```shell
sudo vi /etc/ssh/sshd_config
```

and add these lines

```text
ChallengeResponseAuthentication no
PasswordAuthentication          no
UsePAM                          no
PermitRootLogin                 no
PermitEmptyPasswords            no
```

Restart sshd

```shell
sudo systemctl reload sshd
```

Check that password based login is not allowed

```shell
ssh HOSTNAME -o PubkeyAuthentication=no
```

which should say permission denied.
