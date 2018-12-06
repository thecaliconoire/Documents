# Examples

### Basic structure of an æpp

*__Interactions__*

The purist uses the functions generated out of the Swagger
file. After `create`ing the client and `await`ing it (or use `.then`),
it exposes a mapping of all `operationId`s as functions, converted to
camelCase (from PascalCase). So e.g. in order to get a transaction
based on its hash, you would invoke `client.api.getTx(query)`.

In this way the SDK is simply a mapping of the raw API calls into
Javascript. It's excellent for low-level control, and as a teaching tool to
understand the node's operations. Most real-world requirements involve a series of chain operations, so the SDK provides abstractions for these. The Javscript *Promises* framework makes this somewhat easy.


TO DO: AEN SYSTEM Examples.

### Transaction

Import the required modules.
```js
  import Tx from '@aeternity/aepp-sdk/es/tx/epoch.js'
  import Chain from '@aeternity/aepp-sdk/es/chain/epoch.js'
  import Account from '@aeternity/aepp-sdk/es/account/memory.js'
```

```js
  async function spend (amount, receiver_pub_key) {

    const tx = await Tx({url: 'HOST_URL_HERE'})
    const chain = await Chain({url: 'HOST_URL_HERE'})
    const account = Account({keypair: {secretKey: 'PRIV_KEY_HERE', publicKey: 'PUB_KEY_HERE'}})
    const spendTx = await tx.spendTx({sender: 'PUB_KEY_HERE', receiver_pub_key, amount}))

    const signed = await account.signTransaction(spendTx, 'PUB_KEY_HERE')
    return chain.sendTransaction(signed, opt)

  }
```
The same code, using the SDK abstraction (**high-level**):
First, Import necessary Modules by simply importing the Wallet module.

```js
  import Wallet from '@aeternity/aepp-sdk/es/ae/wallet' // import from SDK es-modules
```

```js
  Wallet({
    url: 'HOST_URL_HERE',
    accounts: [MemoryAccount({keypair: {secretKey: 'PRIV_KEY_HERE', publicKey: 'PUB_KEY_HERE'}})],
    address: 'PUB_KEY_HERE',
    onTx: confirm, // guard returning boolean
    onChain: confirm, // guard returning boolean
    onAccount: confirm // guard returning boolean
  }).then(ae => ae.spend(parseInt(amount), receiver_pub_key))
```

### Contract
This script demonstrates how to Convert Sophia contracts to bytecode, deploy the bytecode to get a callable contract address and how to invoke the deployed contract on the æternity blockchain.

__1.__ Import the main client module `Ae` in the `Universal` flavor from the SDK.

```js
const { Universal: Ae } = require('@aeternity/aepp-sdk')
const program = require('commander')
const fs = require('fs')

function exec (infile, fn, args) {
  if (!infile || !fn) {
    program.outputHelp()
    process.exit(1)
  }

  const code = fs.readFileSync(infile, 'utf-8')
```

__2.__ Most methods in the SDK return _Promises_, so the recommended way of dealing with subsequent actions is `then` chaining with a final `catch` callback.

`Ae` module determines the node's version and rest interface automatically. Only once the Promise is fulfilled, we know we have a working ae client.

Please take note `Ae` is not a constructor but a factory factory, which means it's *not* invoked with `new`.`contractCompile` takes a raw Sophia contract in string form and sends it off to the node for bytecode compilation. This might in the future be done without talking to the node, but requires a bytecode compiler implementation directly in the SDK.

```js
Ae({ url: program.host, debug: program.debug, process }).then(ae => {
    return ae.contractCompile(code)
```
__3.__ Invoking `deploy` on the bytecode object will result in the contract being written to the chain, once the block has been mined. Sophia contracts always have an `init` method which needs to be invoked, even when the contract's `state` is `unit` (`()`). The arguments to`init` have to be provided at deployment time and will be written to the block as well, together with the contract's bytecode.                                        

```js
 }).then(bytecode => {
    console.log(`Obtained bytecode ${bytecode.bytecode}`)
    return bytecode.deploy({ initState: program.init })
```
__4.__ Once the contract has been successfully mined, we can attempt to invoke any public function defined within it. The miner who found the next block will not only be rewarded a fixed amount, but also an amount depending on the amount of gas spend.

```js
}).then(deployed => {
    console.log(`Contract deployed at ${deployed.address}`)
    return deployed.call(fn, { args: args.join(' ') })
```
__5.__ The execution result, if successful, will be an AEVM-encoded result value. Once type decoding will be implemented in the SDK, this value will not be a hexadecimal string, anymore.

```js
}).then(value => {
    console.log(`Execution result: ${value}`)
  }).catch(e => console.log(e.message))
}
```
