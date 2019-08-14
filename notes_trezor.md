# Trezor notes

`https://github.com/trezor`

## Core

### description

Core runs emulator
`./emu.sh`

## Trezor Go (bridge)

run for localhost:21325
`trezord-go -e 21324 -e 21326`
`trezord -e 21324`
`sudo service trezord stop`

## Trezor mcu

after cloning the proyect (to include a custom trezor-common)
`git config -f .gitmodules submodule.vendor/trezor-common.branch master`
`git submodule update --remote`
`git submodule sync`
`git commit -a`
`sudo ./build.sh bl1.6.0 v1.7.0 MEMORY_PROTECT=0`

build emulator with custom firmware
`./build.sh EMU`

run emulator with custom firmware
`build/trezor-emulator-v1.7.0.elf`

install firmware
`trezorctl firmware_update -f build/trezor-TAG.bin`

initialize trezor One
`trezorctl reset-device`

when use a new bootloader and crash after install firmware
comment following lines
https://github.com/trezor/trezor-mcu/blob/master/startup.s#L22-L30

## Python trezor

`trezorctl --help`
`trezorctl sign-message hola --address m/44'/0'/0'/0/0'`

build trezor with custom common
`pip uninstall trezor`
`pip install trezor` internet
`pip install -e .` local
`pip install protobuf`
`python setup.py prebuild`

## trezor-wallet

error by dependency
`npm install eslint-plugin-standard --save`
*link yarn*

run project
`npm install`
`npm run dev`

to use local connect
changed `window.__TREZOR_CONNECT_SRC = 'https://localhost:8088/'` on TrezorConnectActions.js

use
`localhost:8081`

## connect

`git config -f .gitmodules submodule.submodules/trezor-common.branch master`
`git submodule update --init --remote`
`git submodule sync`

install
`yarn`
`yarn run dev`

run on browser console `let result = await TrezorConnect.getAddress({path:"m/44'/0'/0'/0/0'"});`
from html_xsn.html file

## common

- pip install demjson graphviz
- pip install -r tools/requirements.txt

- jsonlint defs/*.json
- jsonlint defs/*/*.json
- python tools/cointool.py check
- python tools/support.py check --ignore-missing
- python protob/graph.py protob/*.proto

## Bitcoin address

address "m/44'/0'/0'/0/0" 1NxrcGa8HnFj1FgYZxzjUdyCv4Au7fLmYw
address "m/44'/0'/0'/0/1" 1JYb731DDFgTBgwcoXVzf8AWsfrBcd9Lsy

## Staknet address

address "m/44'/199'/0'/0/0" XbxUGEVxdpkwUaz9tWuf3HMNFN1u9jXxXB (??? xsn)
address "m/44'/199'/0'/0/1" XtykCTAHXCfVP9tGwvR2jK5tjx1pM9uYmi (??? xsn)

normal fee 0.168 kB / 0.00000168 XSN

`Tpos generated`

tposAddress: 58686f72536f676b42566652506b4353674b343250713437536857434a7157706751
merchantAddress: 58756862586e3941737273646977763732527635524b39525a7642534e54737a486a
comision: 50
signature (signed with "m/44/0/0/0/1" XhorSogkBVfRPkCSgK42Pq47ShWCJqWpgQ tposAddress): 1ffef5ded3075e2b5954a50452496d836a1fcc227545b5385906c91ebe76c336502dfd9a227c8286ed98a086cf910da262cfb401d8f18c3413a42f28457d5265bf
complete:
58686f72536f676b42566652506b4353674b343250713437536857434a715770675158756862586e3941737273646977763732527635524b39525a7642534e54737a486a501ffef5ded3075e2b5954a50452496d836a1fcc227545b5385906c91ebe76c336502dfd9a227c8286ed98a086cf910da262cfb401d8f18c3413a42f28457d5265bf

`signature`
02000000012cf7ab8e32a349cbb888b03ed6d932e7e0745a08a3cdee891723308e14d8c567000000006b483045022100c75c46ea037f00ad15283050597ffbc65cd6cd6a88e229cab212b2de9a77dbd2022048ad9c84a8a932705853990415f3e25db00f58d3cb81062ca1bb479afe485e22012102300f7f79a477b3b3b3c386144e62ecee5ef5111c91859ac41c7786570970a60ffdffffff0300e1f505000000001976a9144e1c4dcc7092c921fa2bffb393851fd37c9a996088ac18ddf505000000001976a9148b1e7b3b08c02e314ae27e0d5b02c518eef238d088ac00000000000000008b6a2258686f72536f676b42566652506b4353674b343250713437536857434a71577067512258756862586e3941737273646977763732527635524b39525a7642534e54737a486a0150411ffef5ded3075e2b5954a50452496d836a1fcc227545b5385906c91ebe76c336502dfd9a227c8286ed98a086cf910da262cfb401d8f18c3413a42f28457d5265bf00000000

## ON EMULADOR

"m/44/0/0/0/1" XhorSogkBVfRPkCSgK42Pq47ShWCJqWpgQ (0.0 XSN)
"m/44/0/0/0/3" XuhbXn9Asrsdiwv72Rv5RK9RZvBSNTszHj (0.0 XSN)
"m/44/0/0/0/4" XqJPr8dwckfeToCkwb9K8H85oEsv6jBTXL (2.0 XSN)

## script tools

curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"hex": "020000000190b066b7b2b8ed416408d3f100da2450a0ba72da32aaf60c458d3d2194666753000000006a47304402203d8db42453f89b2d7912353355e51ce8eef20081414a74c9d9ef36b708e1b72e022075275ca3542d94db684dfbc155918c52edf32b9e38a6fea73333d23eceecf1c70121030c47bc59a802529ce6b4214b0c56dc3d653adb68e378b1a56bfe45cc7db5ec15fdffffff01fc738e06000000001976a9146a610945c5e3465f84b740db8cdc39046e52eb2588ac00000000"}' \
   https://xsnexplorer.io/api/xsn/transactions

./src/xsn-cli sendrawtransaction "010000000134584cece51d7b7068c4bed00d0a45a1d48af697823a71745552c0bc2391cd70000000006a47304402203fddd850d11dc1deab76338cbeef40fc31433b01751305cc91bf98d6c5e9f52602206f7f7113de08cf347568749675df8730fc32d0452341afa5c2bc26ec1a6972520121039844f3d3d53bcdf1293a8ebb6ef879d81998160ec054d42d13a338cac017eae7ffffffff0280969800000000001976a914f6f8e002dd5c80ea2c74b90f863c711cc460f1be88ac0c0c2707000000001976a914381d90aea7a90ab44ee92af95f6657d1f5fccde588ac00000000"

./src/xsn-cli decoderawtransaction 010000000114f1b456001f38e9cf2d57dfd9407282eee2bfb078085238bc40f11435ab0b08000000006b483045022100e955c925c898ed2713f4410fbfe19e49eb653c1bb67be1652ad699d5029da87c0220398e68a412e2d59e3509acc7ecb7087f2cb059a95a7d3571bf082287581033e401210318f058abfbacd88955cd755fcb766cf0866019e89172913ffc0d61830a3af5d9ffffffff02f87b1201000000001976a9148296a5b77770b9d8578f2a1f02f4d633c5dbbfd788ac0000000000000000886a865872796e51377135597276444e326347755235776b7278525676366b455a6f46434e586e624c394d4c597a517644745268784b326461387151353658674a336e5053516450209e7fc11ac688a4754b770aacf53affe7be614a68f07e475003d69697747c0f23688da99ab9afb31db03b7ffb732d431ba41ed2aa79e8a7df4cf90402553d5f62948d125d

## tpos flow

make transaction
send 1 xsn from ownAddress to TposAddres (then signed by ownAddress)
with tpos output with [ TposAddress | MerchantAddress | comision | signedX ]

when
signedX = txid:nout signed with TposAddress

Obtain contract by address
`curl "https://xsnexplorer.io/api/addresses/Xj7rNUXz3yqZY9SmNGte6ummsEAZ3Hh5rL/tposcontracts" | jq .`

## Run Sign Tx By explorer

On block-explorer
`ng serve`
On connect
`npm run dev`
By trezor-go
`trezord -e 21324`
On trezor-mcu
`./build/trezor-emulator-v1.7.3-107-g1b28618.elf`

### check

input
  483bdb594fe347052cb56c60000fba593ef7dee8bf3f069e616fbdf8353e38ae:0
from stakeAddress
  m/44'/199'/0'/0/4
to tposAddress
  XtykCTAHXCfVP9tGwvR2jK5tjx1pM9uYmi
Merchant Address:
  4cf3925dbc5418457176993051acfdb56b9fdc730d14dd6ef635f15c
  (TPOSXbxUGEVxdpkwUaz9tWuf3HMNFN1u9jXxXB)

## AFTER MONOREPO

### FOR LEGACY

- compile emulator
`export EMULATOR=1`
`./script/setup`
`./script/cibuild`
- run emulator
`./firmware/trezor.elf`

### CORE

- requeriments to compile
`cd core`
`sudo apt-get install scons libsdl2-dev libsdl2-image-dev`
- compile emulator
`make vendor`
`make build_unix`
- run emulator
`TREZOR_PROFILE=foobar ./emu.sh`

### PYTHON

- to update common
`python setup.py prebuild`
`pip install -e .`

words
1 switch
2 all
3 hazard
4 online
5 weather
6 approve
7 word
8 omit
9 arctic
10 rate
11 hotel
12 announce

- Test emulator
run emulator
`cd core`
`PYOPT=0 ./emu.sh`
run test
`cd python`
`pytest`
`pytest -k tpos` # only runs tests that have "tpos" in the name

## modified files to add a message to Trezor T

modified:   common/protob/messages-bitcoin.proto
modified:   common/protob/messages.proto

modified:   python/trezorctl
modified:   python/trezorlib/btc.py

modified:   core/src/apps/wallet/__init__.py
modified:   core/src/trezor/messages/MessageType.py
add:        core/src/apps/wallet/<your_file>.py
add:        core/src/trezor/messages/<your_file>.py

### Tpos on CORE

.
.
.

`Tpos`
model T emulator
stakeaddress: Xw9KG53hKepCi58SmHzFxyU46FEbAAVNk9 5877394b473533684b657043693538536d487a4678795534364645624141564e6b39 "m/44'/199'/0'/0/0"
tposaddress: XizKsPmp1fv9CoyeBRSXp75jPg6xpQttKw 58697a4b73506d7031667639436f7965425253587037356a50673678705174744b77 "m/44'/199'/0'/0/1"
merchantaddress: XqJPr8dwckfeToCkwb9K8H85oEsv6jBTXL 58714a5072386477636b6665546f436b7762394b384838356f457376366a4254584c "m/44'/199'/0'/0/2"

`in tx`
txid:vout 8aa2b43bb74ca579c08da494763aa8c0d87a6727893a6c7b88ee2e56e3b1c1f6:0
bip-32 m/44'/199'/0'/0/0
output address XizKsPmp1fv9CoyeBRSXp75jPg6xpQttKw
amount 100000000 (1.0 xsn)
change m/44'/199'/0'/0/0 017990100

sign b'IG3lCzJMxdtiX8k55USU0f901HRqv7pCe7ZlQjK3Z/KeeB/IQWpHyH21XRdMtcrpbeQ6iqaxMv9j45QM8DTiwR4='

`OP_RETURN DETAILS`
58697a4b73506d7031667639436f7965425253587037356a50673678705174744b77
58714a5072386477636b6665546f436b7762394b384838356f457376366a4254584c
50
1f58b9c1a0470849872f22e1d506bca182407eb5962378c3195059709388cf7898075e1f0ca04226ff80c0105582d2c2a4a0cb78f085c0c49f895affb4bbd22758 < digest inv >
`OP_RETURN:`
54504f53434f4e545241435458697a4b73506d7031667639436f7965425253587037356a50673678705174744b7758714a5072386477636b6665546f436b7762394b384838356f457376366a4254584c501f58b9c1a0470849872f22e1d506bca182407eb5962378c3195059709388cf7898075e1f0ca04226ff80c0105582d2c2a4a0cb78f085c0c49f895affb4bbd22758

5861743977677858614a4d614a4557574d5a43473466683542397574425863706261
586572557a7859474735595a7873756968476341594d4459594450543358576b6636
50
1f116a4255fa8cd32418d211227abcb3989684c34c240da876704b229f0a943a7966144f96fbe044b65412fbcb2dee6f28ebe56d1bd5559b4b189cb70beeea8159

`hex`
0200000001f6c1b1e3562eee887b6c3a8927677ad8c0a83a7694a48dc079a54cb73bb4a28a000000006a473044022073512e7e73cd113ecc6cb6906a010427b297cfd9f492ba060e5067839a0a888b0220065bb69aa0fe677920884f2b566fa945b2764008c0c75a116296bd72c3e3bde6012102135ec6c2e464e37b792aa57ad2548b7d7d43dca35638d8dc311994209a911149fdffffff0300e1f505000000001976a9145b0f7b4cf5c800ba78b610a5454bddee6efac62388acd4811201000000001976a914e06439f0666fda63c9472a8fd938f91ad81ad33f88ac00000000000000008b6a2258697a4b73506d7031667639436f7965425253587037356a50673678705174744b772258714a5072386477636b6665546f436b7762394b384838356f457376366a4254584c0150411f58b9c1a0470849872f22e1d506bca182407eb5962378c3195059709388cf7898075e1f0ca04226ff80c0105582d2c2a4a0cb78f085c0c49f895affb4bbd2275800000000

`response`

curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"hex": "010000000114f1b456001f38e9cf2d57dfd9407282eee2bfb078085238bc40f11435ab0b08000000006b4830450221009260c3ce4712ce9f119fe2e156eef376fee85c9f762a454668427c519746cf07022007132e0cae29afa4448fc748c39c750e0c70d06b414368c316e1417afabf11ea01210318f058abfbacd88955cd755fcb766cf0866019e89172913ffc0d61830a3af5d9ffffffff0200e1f505000000001976a914b2b637c60f89fb18b0ac3466c0a5c0f25597067988ac00000000000000008b6a225872796e51377135597276444e326347755235776b7278525676366b455a6f46434e22586e624c394d4c597a517644745268784b326461387151353658674a336e5053516401504120ba4a9e4ec04af894e6e5b3c8bfd822296c4cfc7aeea43659ce8bef7847484c130b0570e4ff8dde7ede05d297b3a36648502d7e6e3dcec7cb5777c3f5b20ba3a726ad1a5d"}' \
   https://xsnexplorer.io/api/xsn/transactions

./src/xsn-cli decoderawtransaction 010000000114f1b456001f38e9cf2d57dfd9407282eee2bfb078085238bc40f11435ab0b08000000006b48304502210082516968ba1afacc642bf7a01c3a9255672f6f103b9ab4ee8c7e9ef8cc7c44fd02201d85b98a514420de51a3a4e21b31073a899a8ba7992adec7cc800a9cbe562eda01210318f058abfbacd88955cd755fcb766cf0866019e89172913ffc0d61830a3af5d9ffffffff0200e1f505000000001976a914b2b637c60f89fb18b0ac3466c0a5c0f25597067988ac00000000000000008b6a225872796e51377135597276444e326347755235776b7278525676366b455a6f46434e22586e624c394d4c597a517644745268784b326461387151353658674a336e505351640150411f6c92842006076d3995a6573891c3be2f4a1f432d75b115525055b6742ad0e0ab5a43853cbea03dc94a629d75a9d1ae50af59b277ef5f122eb0b3b8891abc9f6ad0511a5d

./src/xsn-cli tposcontract validate '{"hex": "010000000114f1b456001f38e9cf2d57dfd9407282eee2bfb078085238bc40f11435ab0b08000000006b483045022100c3e3061c4e1d2939a6d1680d3eeb479d90b08a9c837fefba117d20c39b33b08b0220484e95e7366d0e0599f408f6a01dffbab1ae0081c243ab6b6116c20883f00d7d01210318f058abfbacd88955cd755fcb766cf0866019e89172913ffc0d61830a3af5d9ffffffff0200e1f505000000001976a914b2b637c60f89fb18b0ac3466c0a5c0f25597067988ac00000000000000008b6a225872796e51377135597276444e326347755235776b7278525676366b455a6f46434e22586e624c394d4c597a517644745268784b326461387151353658674a336e5053516401504120ba4a9e4ec04af894e6e5b3c8bfd822296c4cfc7aeea43659ce8bef7847484c130b0570e4ff8dde7ede05d297b3a36648502d7e6e3dcec7cb5777c3f5b20ba3a73b011c5d"}'


./src/xsn-cli tposcontract validate '{"txid": "4ae37fa703bebc8c84fad74825d624fa92daa695b3a2c72db8d0e14ca1a18f57"}'

curl https://xsnexplorer.io/api/addresses/XrynQ7q5YrvDN2cGuR5wkrxRVv6kEZoFCN/tposcontracts | jq .

trezor: ee1e09f74148a6308602412e765be2fb43d513a533d32e887da824d139b00430
cpp: ee1e09f74148a6308602412e765be2fb43d513a533d32e887da824d139b00430

58697a4b73506d7031667639436f7965425253587037356a50673678705174744b77 58714a5072386477636b6665546f436b7762394b384838356f457376366a4254584c 80 1f58b9c1a0470849872f22e1d506bca182407eb5962378c3195059709388cf7898075e1f0ca04226ff80c0105582d2c2a4a0cb78f085c0c49f895affb4bbd22758

### TEST

`required sequence number`
4294967295

`Tpos`
model T emulator

`in tx`
txid:vout 8aa2b43bb74ca579c08da494763aa8c0d87a6727893a6c7b88ee2e56e3b1c1f6:0
bip-32 0
output address XizKsPmp1fv9CoyeBRSXp75jPg6xpQttKw
amount 100000000 (1.0 xsn)
change m/44'/199'/0'/0/0 017990100

sign b'IG3lCzJMxdtiX8k55USU0f901HRqv7pCe7ZlQjK3Z/KeeB/IQWpHyH21XRdMtcrpbeQ6iqaxMv9j45QM8DTiwR4='

`OP_RETURN DETAILS`
5861743977677858614a4d614a4557574d5a43473466683542397574425863706261
586572557a7859474735595a7873756968476341594d4459594450543358576b6636
50
2072974fb637c0b63119167aa6916f46b45368606e540145bc8a41bd53319a762f63c8d42df327e448e8725545ebceb0ad35126cbf8842c8b3b347ed094526f6b0
`OP_RETURN:`
54504f53434f4e54524143545861743977677858614a4d614a4557574d5a43473466683542397574425863706261586572557a7859474735595a7873756968476341594d4459594450543358576b6636502072974fb637c0b63119167aa6916f46b45368606e540145bc8a41bd53319a762f63c8d42df327e448e8725545ebceb0ad35126cbf8842c8b3b347ed094526f6b0

utxo for use:
0 Xe2cLLPxqahT3XkkuuPJrAXhsved39jeqa
1 Xat9wgxXaJMaJEWWMZCG4fh5B9utBXcpba
1.11994500 XSN
TPOS 5861743977677858614a4d614a4557574d5a43473466683542397574425863706261586572557a7859474735595a7873756968476341594d4459594450543358576b6636501f116a4255fa8cd32418d211227abcb3989684c34c240da876704b229f0a943a7966144f96fbe044b65412fbcb2dee6f28ebe56d1bd5559b4b189cb70beeea8159
txid:vout 6b97a5579b4e088d472c1b8c2a30b216be1603dd006af7a42d75c12b0a75d6db:0


### Protoc in Path

Prerequesites\
`sudo apt-get install autoconf automake libtool curl make g++ unzip`

Installation

From this [page](https://github.com/protocolbuffers/protobuf/releases/tag/v3.6.1), download the protobuf-all-[VERSION].tar.gz.\
Extract the contents and change in the directory

```
./configure
make
make check
sudo make install
sudo ldconfig # refresh shared library cache.
```
Check if it works\
`protoc --version`
```
libprotoc 3.6.1
```