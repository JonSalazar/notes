# NOTES

## client

Run Web-ui
`ng serve`

If it doesn't recompile when save changes, try:
`ng serve --poll=2000`

```sh
**Browser**
localhost:4200
```

## SERVER

Run test in /server
`DOCKER_HOST=localhost4243 sbt test`

Run /server
`sbt run`

## XSN

Run server:
`bin/xsnd -txindex -rpcport=51473 -rpcuser=dummy -rpcpassword=replaceme`

Run UI:
`./bin/xsn-qt`

Get legacy address on debug
`getnewaddress label legacy`
example `Xj5mEprwQpNYBFTWeuHabNyJB8CDTWZ6Vw`

To compile binary
`./autogen.sh`
`./configure`
`make`
`make install` # optional

If it fail to run `make` for openssl dependency
`cd $OPENSSL_PATH`
`export OPENSSL_PREFIX=/usr/local/ssl/`
`CC='cc -fPIC' ./config --prefix=$OPENSSL_PREFIX`

Get into docker image to run xsn
`sudo docker run -it -v $(pwd):/home/xsn/src:z -v $HOME/.xsncore:/home/xsn/.xsncore:z "xsn"`
`cd /home/xsn/src/`

Run xsnd from image in background
`./src/xsnd -daemon`

command
`./src/xsn-cli getblockchaininfo`
`./src/xsn-cli signrawtransaction`
`./src/xsn-cli decoderawtransaction`
`./src/xsn-cli tposcontract validate '{"txid": "c04776bcd2c83c4946dcd1e1ce4c1c97991fbc517c90f60ad18260af4275ff2d"}'`
`./src/xsn-cli signmessage "address" "message"`

./src/xsn-cli signmessage XfH4bMsoizp8VnwduKjR6cc7dGKZFf3oqh hola

Expected format: tposcontract validate
`{ "hex" : "hex_encoded_transaction", "check_spent" : 1, (optional, default 1) "check_signature" : 1 (optional, default 1) }`
`{ "txid" : "txid", "check_spent" : 1, (optional, default 1) "check_signature" : 1 (optional, default 1) }`
Example
xsn-cli tposcontract validate '{ "hex" : "01000000010bf43835745a4b2a92fbac381db7a1d9256c2c0a34ec8a0b0242e2474a106a42000000006a47304402200a8428ef0a614f3cd0e35d47494481b48cff02ecd2ad92df2c356311c305367302207b17c35126c88034780bf203e94a939cc5de276488ae28337edaffd173744f7501210283588ca5fe2454f05ac631cd1e2bd530ea2bfb4665c70cccd3860dbdda5a0534ffffffff02a0860100000000001976a9140decc6a944bbe368a52f7a299a62589606250cde88ac74fb0607000000001976a914c8a4a1cb23d7b08ae36658e0cad60c5bcd85e08e88ac00000000"}'

stop
`./src/xsn-cli stop`

## SBT Commands

`sudo sbt clean`

`sbt`
`testOnly <use tab looking for the test>`

```sh
**Browser**
localhost:9000
```

## Docker

Get docker containers
`curl localhost:4243/containers/json`

## Postgresql

`install`
first install the 9.6 version
`http://devopspy.com/linux/install-postgresql-9-6-ubuntu-16-04-lts/`
then
`https://www.postgresql.org/download/linux/ubuntu/`

Postgres login
~ Was changed **/etc/postgresql/9.6/main/pg_hba.conf** METHOD peer -> trust
~ Restart postgresql `sudo service postgresql restart`
`psql -U postgres`

check current services
`pg_lsclusters`

~ Was created database xsn_blockchain

Commands:

```sh
\l -> show databases
\d -> show tables
\connect ${ name_database } -> use database (used xsn_blockchain)
\q -> exit
```

## Git

Add remote url
`git remote add fork ${ destiny } (used https://github.com/X9Developers/block-explorer.git)`
