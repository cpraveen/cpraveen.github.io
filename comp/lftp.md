---
layout: default
---

# LFTP

LFTP is a file transfer program that can use ftp, sftp, etc.

To set your lftp prompt, see my [lftp settings file](https://github.com/cpraveen/cfdlab/blob/master/configs/lftprc.txt), which you should copy as `$HOME/.lftprc` file.

To connect to a server using sftp

```shell
lftp sftp://USERNAME@SERVER
```

Some basic commands are listed below.

```text
ls                   | List remote dir (this is cached)
rels                 | List remote dir (not cached)
pwd                  | show remote dir
cd DIR               | change remote dir to DIR

!ls                  | List contents of local dir
lpwd, !pwd           | show local dir
lcd DIR              | change local dir to DIR

get foo.txt          | get foo.txt
pget -n 2 foo.txt    | get foo.txt with 2 parallel connections

mget *.txt           | get all .txt files
mget -c *.txt        | get all .txt files that do not exist locally
mget -d DIR/*.txt    | get all .txt files and make DIR locally

mirror               | sync remote dir to local dir
mirror -c            | incrementally sync remote dir to local dir
mirror DIR           | sync remote DIR to local
mirror -c DIR        | sync remote DIR to local incrementally
```
