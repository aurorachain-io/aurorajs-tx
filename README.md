# package.json [usage example]

```javascript
"dependencies": {
  'aurorajs-tx': 'aoaio/aurorajs-tx',
  ...
}
```


# USAGE

```javascript
const AuroraTx = require('aurorajs-tx')
const privateKey = Buffer.from('e331b6d69882b4cb4ea581d88e0b604039a3de5967688d3dcffdd2270c0fd109', 'hex')
const chainId = 1

function AOAtoHex(address) {
    return address.replace(/^AOA/, '0x')
}

const txParams = {
  nonce: '0x00',
  gasPrice: '0x09184e72a000', 
  gasLimit: '0x2710',
  to: AOAtoHex('AOA0000000000000000000000000000000000000000'), 
  value: '0x00', 
  data: '0x7f7465737432000000000000000000000000000000000000000000000000000000600057',
  action: 0, // 0 for regular/asset transaction, 6 for call contract
  asset: AOAtoHex('AOA0000000000000000000000000000000000000000'), //asset id, use it when asset transaction
  subAddress: 'AOA140e0b100bc3c5820a5d5ed3cf94d54491f51a2fb590033560f603659600033565733600'

const tx = new AuroraTx(txParams)
tx.sign(privateKey, chainId)
const serializedTx = tx.serialize()
```

**Note:** this package expects ECMAScript 6 (ES6) as a minimum environment. From browsers lacking ES6 support, please use a shim (like [es6-shim](https://github.com/paulmillr/es6-shim)) before including any of the builds from this repo.

