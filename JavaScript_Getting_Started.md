
_Epoch_ is the reference implementation model for æternity. Epoch is implemented in Erlang. The SDKs allow for communication with the Epoch and are written in [__Javascript__](https://github.com/aeternity/aepp-sdk-js), [__Python__](https://github.com/aeternity/aepp-sdk-python) and [__GO__](https://github.com/aeternity/aepp-sdk-go).

# __Getting Started: Javascript SDK__

## Introduction

The Javascript SDK assumes you have read through the [Protocol Guide](https://github.com/aeternity/protocol). The SDK allows users to utilize the æternity blockchain for various different projects including building æpps, deploy contract, and create transactions. If you have feedback on what we should do to improve the SDKs, please email us at aepp-dev@aeternity.com, to let us know. As we value your input.

There are three different ways of incorporating aepp-sdk-js into your project, depending on the particular scenario:

* ES Modules at es/ (recommended)
* Node.js bundle at dist/aepp-sdk.js
* Browser bundle at dist/aepp-sdk.browser.js

Also, please be aware that using require instead of module loader syntax (import) means that the default export automatically becomes exposed as default, which is reflected below in the code examples. This is due to a recent change in Babel compilation and fully compliant with the standard.
## Requirements
* [Node.js](https://nodejs.org/en/download/)
* [Webpack4](https://webpack.js.org/): a modern bundler which understands ES2015
* [Babel](https://babeljs.io/):  a compiler which translates the subset of ES used by aepp-sdk will have  to be used
## Installation

To install the SDK as a Node.js package from the [Javascript SDK](https://github.com/aeternity/aepp-sdk-js) repository and ```cd``` into your working directory on your local machine and execute one of the following commands:

```js
npm install @aeternity/aepp-sdk
```
or

```js
pnpm i @aeternity/aepp-sdk
```
or

```js
yarn i @aeternity/aepp-sdk@next
```

If the user desires to install a _Pre-Release_ (latest `beta` or `alpha` version) using the latest Epoch version, you have to install the package appending the `@next` tag reference.

```js
npm install @aeternity/aepp-sdk@next
```

You can also add a development version from GitHub by dropping the `@` and adding `#` and a branch name at the end, for example

```npm install aeternity/aepp-sdk#develop```.

The recommended approach to using aepp-sdk is to import one of the following _Ae Factories_ based on the specific use case:


```js
import Aepp from '@aeternity/aepp-sdk/es/ae/aepp'
```
__*(The Aepp Flavor is Recommended)*__

or

```js
import Wallet from `@aeternity/aepp-sdk/es/ae/wallet`
```
or

```js
import Universal from '@aeternity/aepp-sdk/es/ae/cli](api/ae/universal.md)'
```

# Creating an account with the SDK:

After you have added the SDK you can then create an account using the Javascript SDK.
```js
./bin/aecli.js account create TEST.json
```
You will be prompted to enter your new account password. After the password is entered, you can now fill your account with AE Tokens using the Faucet Aepp.
To do this first retrieve your account address.

```js
./bin/aecli.js account address TEST.json
```

The [Faucet Aepp](https://faucet.aepps.com/) will top off your account with AE Tokens.

After a user has an account an instance can be created.

```js
const ae = Aepp()
```
Now start interacting with the blockchain.

```js
ae.then(ae => ae.height()).then(h => console.log(h))
```

**IMPORTANT:** Check out the [Usage Documentation](docs/usage.md) to avoid any unexpected difficulties.

### Hacking
For advanced use, development versions and to get a deeper understanding of the
SDK, it is advised to read the [hacking documentation](hacking.md) documentation.

### Change Log
For the changes that have taken place within the sdk please read the
[Change Log](https://github.com/aeternity/aepp-sdk-js/blob/develop/CHANGELOG.md)
