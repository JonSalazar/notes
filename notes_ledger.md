# LEDGER

## used seed for test

1 scare
2 win
3 wheat
4 dice
5 topic
6 assist
7 stool
8 render
9 top
10 uniform
11 major
12 thrive
13 trouble
14 endorse
15 sentence
16 term
17 awake
18 cradle
19 field
20 cabbage
21 poverty
22 object
23 mistake
24 second


## installing dependencies for Ledger Apps

follow `https://ledger.readthedocs.io/en/latest/userspace/getting_started.html`
export BOLOS_SDK=/media/kev/Big1/ww/nanos-secure-sdk
export BOLOS_ENV=/media/kev/Big1/ww/bolos-devenv

use python tools (`https://github.com/LedgerHQ/blue-loader-python`) for
`cd /media/kev/Big1/ww/`
source ledger/bin/activate

solving PIL dependency problem
`pip install --upgrade pip`

## install lib-ledger-core-build

follow `https://github.com/LedgerHQ/lib-ledger-core`
`cd lib-ledger-core-build`
`cmake -DCMAKE_INSTALL_PREFIX=/usr/lib/x86_64-linux-gnu/qt5 ../lib-ledger-core && make`

## Run ledger-app-btc

get correct clang
connect device (install only on a non installed device)
```
cd ledger-app-btc
export BOLOS_SDK=/media/kev/Big1/ww/nanos-secure-sdk
export BOLOS_ENV=/media/kev/Big1/ww/bolos-devenv
make all
```

## Debuger firmware

`https://ledger.readthedocs.io/en/latest/userspace/debugging.html?highlight=log`
download from above
`blup_0.9_misc_m1.hex`
`mcu_1.7-printf_over_0.9.hex`
`mcu_1.7_over_0.9.hex`

`cd ledger`
`python -m ledgerblue.loadMCU --targetId 0x01000001 --fileName blup_0.9_misc_m1.hex --nocrc`
`python -m ledgerblue.loadMCU --targetId 0x01000001 --fileName mcu_1.7-printf_over_0.9.hex --reverse --nocrc`

install normal firmware
`python -m ledgerblue.loadMCU --targetId 0x01000001 --fileName mcu_1.7_over_0.9.hex --reverse --nocrc`

On ./usbtool to read log messages
`./usbtool -v 0x2c97 log`

## Script html for blue-loader-python

Build html documentation
`cd blue-loader-python/doc`
`make html`
`build/html/index.html`

## STACK LEDGER APP

> ledger-app-btc: is the app in device 
`make load`
`make load COIN=xsn`

> ledgerjs/packages/hw-app-btc: is the library bridge between app and customer 
`yarn build`

> if it fails, ensure to use 8.12.0 node version
ledgerjs-examples: is a number of examples using app through the library 
`yarn` 
`yarn start`
probably is needed `libusb` dependency

## HTML
use npm and install dependencies `npm install <dependency>`
copy the code examples (writen in Typescript) and compile with `tsc typescript.file`
use browserify to budnle the javascript files `browserify jsfiles.js -o bundle.js`
use on html <script src="bundle.js"></script>

(if you find the regeneratorRuntime error) include `npm install --save @babel/polyfill` dependency and call it 
at the start of ts file

add permission to usb 
`navigator.usb.requestDevice({filters:[]}).then(function(device){ console.log(device); });`
after that you should find it with this
`navigator.usb.getDevices().then(function(devices){ console.log(devices); });`
if not you have a problem

## Ledger Address info
Xx5Ab8X7t34NVRiwraF3ybqhepVQU3wqiD "44'/199'/0'/0/0" 
XyH6jgSgxe2zXErKtNrZTkoJrECyQkswMA "44'/199'/0'/0/2"

49'/384'/0'/0/0
m/84'/199'/0'/0/0 (losed?) 99989160 
7oxE3UNq8jApzk5NjrcoWrZYnkPRtuwPaU 

finally both verified
49'/384'/0'/0/1 sended 17989100 but was put it on XeJM2vNSQuY25MGjHy7DnVtCpNwzsgruaz :(
7W29xQV9p5jT1LuXpo86gyZ147VQE36Nm5

I don't know why but the Tx give the money to
path ?? (17989100)
XeJM2vNSQuY25MGjHy7DnVtCpNwzsgruaz

44'/384'/0'/0/0
XkPKhnKxCghRk3Ygtt19PqskX2ctVpeqE5 (119998600) (1.1... XSN)

44'/384'/0'/0/1
XrynQ7q5YrvDN2cGuR5wkrxRVv6kEZoFCN

> Tpos building

ascii address, TPOS (XrynQ7q5YrvDN2cGuR5wkrxRVv6kEZoFCN)(44'/384'/0'/0/1): `5872796e51377135597276444e326347755235776b7278525676366b455a6f46434e`
ascii address, Merchant (XnbL9MLYzQvDtRhxK2da8qQ56XgJ3nPSQd)(44'/384'/0'/0/2): `586e624c394d4c597a517644745268784b326461387151353658674a336e50535164`
comision: `50` (80 dec)
sign: 080bab3514f140bc38520878b0bfe2ee827240d9df572dcfe9381f0056b4f114:0
with: (44'/384'/0'/0/1) XrynQ7q5YrvDN2cGuR5wkrxRVv6kEZoFCN
signature: 
// 65
`20ba4a9e4ec04af894e6e5b3c8bfd822296c4cfc7aeea43659ce8bef7847484c130b0570e4ff8dde7ede05d297b3a36648502d7e6e3dcec7cb5777c3f5b20ba3a7`

`20d3fede4fb2e8c84d110bdbd0138e89b43a8ecbf7e939ab2c067de41c3999c3dd0bf7991e6abb24fda3d522b7e8f74c972cd449e3787eff73cdfebdfe3f6e4f06`
TPOS: `5872796e51377135597276444e326347755235776b7278525676366b455a6f46434e586e624c394d4c597a517644745268784b326461387151353658674a336e505351645020ba4a9e4ec04af894e6e5b3c8bfd822296c4cfc7aeea43659ce8bef7847484c130b0570e4ff8dde7ede05d297b3a36648502d7e6e3dcec7cb5777c3f5b20ba3a7`

txid Tpos contract
`4ae37fa703bebc8c84fad74825d624fa92daa695b3a2c72db8d0e14ca1a18f57`

### trezor address 

"m/44'/199'/0'/0/0"
Xw9KG53hKepCi58SmHzFxyU46FEbAAVNk9

### testing