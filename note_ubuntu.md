# Ubuntu

Disable input device
`xinput set-prop 12 "Device Enabled" 0`

## Git

verify remote origin
`git remote -v`

use a fork of git submodule
change .gitmodules file
`git submodule sync`

download submodules
`git submodule update --recursive --remote`
for first time
`git submodule update --init --recursive`

set custom submodule to building branch
`git config -f .gitmodules submodule.<path>.branch <branch>`
`git submodule update --remote`

when change submodule commit and is it needed to rehash sha1 on main project
`git commit -a`

Update changes or message for the last commit
`git commit --amend`
Update old commit message
n = number of commit to check back
`git rebase -i HEAD~n`
after use the command change `pick` for `reword` on the interested commit and save

managin remote
`git remote add origin <path url>`
`git remote add fork <path url>`
`git remote remove [origin|fork]`

revert recent commit, put the commited files as untraked files
`git reset HEAD^`

for sign commits (consider that must have the user.name and user.email consistent with key)
install `sudo apt install gnupg2`
see list `gpg2 --list-keys --keyid-format LONG`
generate key `gpg2 --gen-key`
export public key to register in github `gpg2 --armor --export <EMAIL>`
to git use gpg2 `git config --global gpg.program gpg2`
inside the project specify to use current key `git config user.signingkey BAEF3C52144D83E4` and `git config commit.gpgsign true`
sign commits `git commit -s` or if it was already commited `git commit --amend -s`
to change autor `git commit --amend --author="<NAME> <<EMAIL>>"`

## pyenv

Put local python version
`pyenv install <VERSION>`
`cd folder`
`pyenv local <VERSION>`
`pyenv rehash`
`python --version`

if build fail for openssl dependencies use
`https://github.com/pyenv/pyenv/wiki/common-build-problems`
(for ubuntu)
`sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python-openssl git`
next
(using the absolute path where openssl was installed)
`LDFLAGS="-L/usr/local/ssl/lib" CFLAGS="-I/usr/local/ssl/include" pyenv install -v <VERSION>`

## test

address bitcoin 1MTV2RUq9hHunRoVKTNAoXM8PozgJ45uZQ

trezorctl firmware_update -f build/bootloader-bl1.6.0.bin

## docker

installing docker from
> https://www.digitalocean.com/community/tutorials/como-instalar-y-usar-docker-en-ubuntu-16-04-es

add user to group

sudo usermod -aG docker katze
sudo gpasswd -a katze docker

## on it

transaction.h .c
fsm_msg_coin.h
fsm.h
signing.c [ signing_txack ]
messages-bitcoin.pb.h
pb.h

## Disable CORS on Chrome

`google-chrome --disable-web-security`

## get thumbnail from youtube

`https://i.ytimg.com/vi/<ID YOUTUBE VIDEO>/maxresdefault.jpg`
or
`ctrl + u`
`ctrl + f` -> `\/hqdefault.jpg`
from complete url remove `\` and go to link
for max resolution change `hqdefault` to `maxresdefault`

## bashrc

make non case sensitive autocomplete on bash
`echo set completion-ignore-case on | sudo tee -a /etc/inputrc`

## Vim

:q to exit
:wq save and quit
:%!xxd to see hex format
:%!xxd -r to restore ascii format
/ to find a word
i to edit text

## Nvm 
for nvm bash variable
```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
```

`nvm ls` see available versions
`nvm current` see current version of node
`nvm install <version>` to install version of node
`nvm use <version>` change current version of node


## Typescript

compile js
`tsc jsfile.js`

if have this error 
> An async function or method in ES5/ES3 requires the 'Promise' constructor`
include a tsconfig.json file with `"lib": [ "es2015" ]` on it


## Hard drive issues

to check partitions
`lsblk`

for problem 
```
mount: wrong fs type, bad option, bad superblock on /dev/sdc2,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```
use
` sudo e2fsck -f -b 32768 -y /dev/<Partition e.g. sdc2>`
