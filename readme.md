# OpenTrade is the best opensource cryptocurrency exchange!

Live version https://exchange.flamecoin.co

```
git clone https://github.com/srandd/opentrade
cd opentrade
npm install
node main.js
```

In the browser open up https://localhost:443

The first registered user will be exchange administrator. 

## Edit ~/opentrade/server/modules/private_constants.js !!

```
'use strict';

exports.recaptcha_priv_key = 'YOUR_GOOGLE_RECAPTCHA_PRIVATE_KEY';
exports.password_private_suffix = 'LONG_RANDOM_STRING1';
exports.SSL_KEY = '../ssl_certificates/privkey.pem'; //change to your ssl certificates private key
exports.SSL_CERT = '../ssl_certificates/fullchain.pem'; //change to your ssl certificates fullchain

exports.walletspassphrase = {
    'MC' : 'LONG_RANDOM_STRING2',
    'BTC' : 'LONG_RANDOM_STRING3',
    'DOGE' : 'LONG_RANDOM_STRING4'
};
```

# Add trade pairs

For each coin you should create *.conf file
This is common example for "some_coin.conf"

```
rpcuser=long_random_string_one
rpcpassword=long_random_string_two
rpcport=12345
rpcclienttimeout=10
rpcallowip=127.0.0.1
server=1
daemon=1
upnp=0
rpcworkqueue=1000
enableaccounts=1
litemode=1
staking=0
addnode=1.2.3.4
addnode=5.6.7.8

```

Also you must encrypt wallet.dat by the command

```
./bitcoind encryptwallet random_long_string_SAME_AS_IN_FILE_private_constants.js

```

*If coin is not supported encryption (like ZerroCash and it forks) then coin could not be added to the OpenTrade*


When coin daemons will be configured and started

1. Register on exchange. The first registered user will be exchange administrator.
2. Go to "Admin Area" -> "Coins" -> "Add coin"
3. Fill up all fields and click "Confirm"
4. Fill "Minimal confirmations count" and "Minimal balance" and uncheck and check "Coin visible" button
5. Click "Save"
6. Check RPC command for the coin. If it worked then coin was added to the exchange!

All visible coins should be appear in the Wallet. You shoud create default coin pairs now.

File ~/opentrade/server/constants.js have constant that you can change

https://github.com/3s3s/opentrade/blob/master/server/constants.js#L5

```
exports.TRADE_MAIN_COIN = "Marycoin"; //change Marycoin to your main coin pair
exports.TRADE_DEFAULT_PAIR = "Litecoin"; //change Litecoin to your default coin pair
exports.TRADE_COMISSION = 0.001; //change trade comission percent

exports.recaptcha_pub_key = "6LeX5SQUAAAAAKTieM68Sz4MECO6kJXsSR7_sGP1"; //change to your recaptcha public key

exports.NOREPLY_EMAIL = 'no-reply@multicoins.org'; //change no-reply email
exports.SUPPORT_EMAIL = 'ivanivanovkzv@gmail.com'; //change to your valid email for support requests
exports.my_portSSL = 40443; //change to your ssl port

```

After that you coins should appear on the main page.


