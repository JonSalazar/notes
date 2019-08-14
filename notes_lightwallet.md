#Light wallet

private repository
`https://github.com/bwang22/lightWallet`

install at least qt 5.12.2
`https://wiki.qt.io/Install_Qt_5_on_Ubuntu`
BUT! look for and download this instead `qt-unified-linux-x64-3.1.1-online.run`

possible dependencies
`sudo apt-get install libevent-dev`
`sudo apt-get install qtdeclarative5-dev`

install last cmake `https://peshmerge.io/how-to-install-cmake-3-11-0-on-ubuntu-16-04/`
`sudo apt-get install libsnappy-dev`
`sudo apt-get install libdb4.8`

probably it's needed python 2.7.11

build dependencies
`cd depends`
`./build-dependencies.sh <ABSOLUTE_PATH>/lightWallet/modules` `(./build-dependencies.sh /media/kev/Big1/ww/lightWallet/modules)`

update submodules
`git submodule update --remote --init`

to compile run
`qmake`
`qmake src.pro`
`and then make`


 