eclair-rpc.js
===============

A client library to connect to eclair RPC in JavaScript. Forked of [Bitpay's bitcoind-rpc](https://github.com/bitpay/bitcoind-rpc).

## Get Started

eclair-rpc.js runs on [node](http://nodejs.org/), and can be installed via [npm](https://npmjs.org/):

```bash
npm install eclair-rpc
```

## Configure eclair node
Install [eclair](https://github.com/ACINQ/eclair) and make sure eclair API is running and reachable. Example `.eclair/eclair.conf` file might look like:

```
eclair.chain=testnet
eclair.node-alias=testone
eclair.node-color=49daaa


eclair.bitcoind.rpcport=18333
eclair.bitcoind.rpcuser=bitcoind_username
eclair.bitcoind.rpcpassword=bitcoind_password


eclair.api.enabled=true
eclair.api.password="eclair_password"

eclair.api.binding-ip="0.0.0.0"
```

### Warning: Exposing your node's API externally is not safe and should be limited to testnets only!

## Examples

```javascript
var run = function() {
  var EclairClient = require('eclair-rpc');

  var config = {
    protocol: 'http',
    pass: 'password',
    host: '127.0.0.1',
    port: '8080',
  };

  var rpc = new EclairClient(config);

  var txids = [];

  function getNodeInfo() {
    rpc.getinfo(function(err, res){
      if (err) {
        console.error(err);
      }
      console.log(res);
    });
  }

  getNodeInfo();
};
```

## Supported callspec
```javascript
RpcClient.callspec = {
  allnodes: '',
  channels: '',
  checkinvoice: 'str',
  close: 'str',
  connect: 'str str int',
  getinfo: '',
  open: 'str int',
  receive: 'int str',
  send: 'str',
};

```

## License

**Code released under [the MIT license]https://github.com/zeltsi/eclair-rpc/blob/master/LICENSE).**
