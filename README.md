# Mobile-wallet-code

K-js-sdk
Javascript SDK for KWallet

You can open it in the KWallet DAPP Browser.

Installation
npm
Install

npm install KWallet
Require module

var Kwallet = require('KWallet');
html
Drop the dist/KWallet.min.js bundle into your html project

<script src="path/to/KWallet.min.js"></script>
Get instance

var KWallet = window.KWallet;
Usage
Note

Note: The SDK needs to be used in the KWallet DAPP Browser.

Common

Common method for KWallet DAPP Browser

isK
Kwallet.isK();
Return

true
getAppInfo

Get user KWallet info

KWallet.getAppInfo().then(console.log);
Return

{
  "name": "K Wallet",
  "client": "iOS",
  "version": "1.0.0",
  "deviceId": "2FB1AD00-20C7-45FF-AE94-A2F30A02F8F6"
}
openUrl

Open a new webview tab

KWallet.openUrl("http://www.kajino.jp/").then(console.log);
Return

{
  "result": 1
}
openThirdApp

KWallet.openThirdApp("tel:110").then(console.log);
Return

{
  "result": 1
}
close

Close window

KWallet.close().then(console.log);
Return

{
  "result": 1
}
back

Back to previous page

KWallet.back().then(console.log);
Return

{
  "result": 1
}
fullScreen

Set full screen
0 - normal screen
1 - full screen

KWallet.fullScreen(1).then(console.log);
Return

{
  "result": 1
}
orientation

Set screen orientation
0 - portrait
1 - landscape

KWallet.orientation(1).then(console.log);
Return

{
  "result": 1
}
getLanguage

Get user app language

KWallet.getLanguage().then(console.log);
Return

"cn"
getWalletType

Get user current wallet type

KWallet.getWalletType().then(console.log);
Return

"BTC"
getCurrentWallet
Get user current wallet info

Kwallet.getCurrentWallet().then(console.log);
Return

{
  "blockchain":"K",
  "nickname":"KAJINObp",
  "address":"KAJINObp",
  "authority":"active"
}
getWalletsWithType

Get user wallets of the type

Kwallet.getWalletsWithType("K").then(console.log);
Return

[
  {
    "nickname":"KAJINObp",
    "address":"KAJINObp"
  },
  {
    "nickname":"KAJINObb",
    "address":"KAJINObb"
  }
]
postCustomMessage

For other custom action

Kwallet.postCustomMessage(method, payload);
BTC Wallet

BTC wallet method for KWallet DAPP Browser

BTC.transfer

Send BTC transaction

Kwallet.BTC.transfer(from, amount, to, memo).then(console.log);
OR

let transaction = {
  from : from,
  amount : amount,
  to : to,
  memo : memo
}
Kwallet.BTC.transfer(transaction).then(console.log);
Return

{
  "result":"trxid" // transaction hash
}
ETH Wallet

ETH wallet method for KWallet DAPP Browser

ETH.transfer

Send ETH transaction

Kwallet.ETH.transfer(from, amount, to, memo).then(console.log);
OR

let transaction = {
  from : from,
  amount : amount,
  to : to,
 
}
Kwallet.ETH.transfer(transaction).then(console.log);
Return

{
  "result":"trxid" // transaction hash
}
ETH Wallet

ETH wallet method for KWallet DAPP Browser

Note: KWallet is already compatible with Scatter. You can use Scatter to build your K DAPP

ETH.init

Please initialize BP information before using the other method

let config = {
  "nodes":[

    // 0: testnet-node
    {
      "jsonRpc":"https:\/\/ethtestnet.kajino.jp",
      "chainID":"cf057bbfb72640471fd910bcb67639c22df9f92470936cddc1ade0e2f2e7dc4f"
    },

    // 1: testnet-node
    {
      ,
      "chainID":"aca376f206b8fc25a6ed44dbdc66547c36c6c33e3a119ffbeaef943642f0e906"
    }

  ]
};
Kwallet.ETH.init(config);  //return true
ETH.getAccount

Get current account info, must use getAccount() before using the other method.

Kwallet.ETH.getAccount().then(console.log);
ETH.get_info

Get block info

Kwallet.ETH.get_info().then(console.log);
ETH.abi_json_to_bin

JSON to Bin

Kwallet.ETH.abi_json_to_bin(data).then(console.log);
ETH.signTransaction

Sign transaction

Kwallet.ETH.signTransaction(transaction).then(console.log);
ETH.push_transaction & ETH.push_transaction_all

Push transaction

Kwallet.ETH.push_transaction(transaction,signatures,compression).then(console.log);
OR

Kwallet.ETH.push_transaction_all(data).then(console.log);
ETH.customSignProvider

Custom Sign Provider, for plugin like eth.js

// eth.js
eth({
  httpEndpoint: "https://path/to/node",
  chainId:      "aca376f206b8fc25a6ed44dbdc66547c36c6c33e3a119ffbeaef943642f0e906",
  signProvider: Kwallet.ETH.customSignProvider,
});
ETH.geteth

Get eth.js instance which node httpEndpoint and signProvider have been initialized. Please include the eos.js plugin first.

<script src="http://path/to/eth.js"></script>
<script>
var eth = Kwallet.ETH.getEth();

//do something with eth.js
eths.getBlock(1);
</script>
