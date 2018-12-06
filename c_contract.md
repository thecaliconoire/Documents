# CONTRACT

```python
from aeternity.aevm import pretty_bytecode
```
aeternitys virtual machines ```pretty_bytecode``` allows for the creation of readable hexdecimal hashes instead of binary bytecodes.

```python
from aeternity.openapi import OpenAPIClientException
```
Allows for more readable versions of JSON, YAML and Swagger files.

```python
from aeternity import utils, config
```
We import aeternitys utils module and the config module. The config module will be referenced
too call the contracts default settings.

```python
class ContractError(Exception):
    pass


contract lifecycle is set to the default settings
compile contract (get the bytecode)
deploy the contract (get the address)
encode the calldata (get the )

```
First the class Contract is created and we assign Ethereum Machine, and
Sophia, aeternitys contract language to the class, so that the contract is then
assigned too the EVM and Sophia.

```python
class Contract:
    EVM = 'evm'
    SOPHIA = 'sophia'

The init function allows for initialize a contract object.
If the bytecode is not provided it will be computed using the compile command.

Some terms to keep in mind within the contract init function:
parameter source_code: the source code of the contract
parameter bytecode: the bytecode of the contract
parameter address: the address of the contract
parameter application Binary Interface (abi): The abi, default 'sofia'
parameter client: The epoch client to use.

    def __init__(self, source_code, client, bytecode=None, address=None, abi=SOPHIA):
        """
        Initialize a contract object

        if bytecode is not provided it will be computed using the compile command.

        :param source_code: the source code of the contract
        :param bytecode: the bytecode of the contract
        :param address: the address of the contract
        :param abi: the abi, default 'sofia'
        :param client: the epoch client to use
        """
        self.client = client
        self.abi = abi
        self.source_code = source_code
        self.bytecode = bytecode
        self.address = address
        if self.bytecode is None:
            self.bytecode = self.compile(self.source_code)
```
The ```tx_call``` function allows for a Sophia contract to be called.
The contracts settings are set too config defaults. A value error is raised if a
contract is missing.

```python
    def tx_call(self, account, function, arg,
                amount=config.CONTRACT_DEFAULT_AMOUNT,
                gas=config.CONTRACT_DEFAULT_GAS,
                gas_price=config.CONTRACT_DEFAULT_GAS_PRICE,
                fee=config.DEFAULT_FEE,
                vm_version=config.CONTRACT_DEFAULT_VM_VERSION,
                tx_ttl=config.DEFAULT_TX_TTL):
          """Call a sophia contract"""

        if not utils.is_valid_hash(self.address, prefix="ct"):
            raise ValueError("Missing contract id")

        try:
            # prepare the call data
            call_data = self.encode_calldata(function, arg)
            # get the transaction builder
            txb = self.client.tx_builder
            # get the account nonce and ttl
            nonce, ttl = self.client._get_nonce_ttl(account.get_address(), tx_ttl)
            # build the transaction
            tx = txb.tx_contract_call(account.get_address(), self.address, call_data, function, arg, amount, gas, gas_price, vm_version, fee, ttl, nonce)
            # sign the transaction
            tx_signed, sg, tx_hash = self.client.sign_transaction(account, tx)
            # post the transaction to the chain
            self.client.broadcast_transaction(tx_signed, tx_hash)
            # unsigned transaction of the call
            call_obj = self.client.get_transaction_info_by_hash(hash=tx_hash)
            return tx, tx_signed, sg, tx_hash, call_obj
        except OpenAPIClientException as e:
            raise ContractError(e)
```
Create a contract transaction, then broadcast the transaction too the chain.
This is an asynchronous processes. Meaning the processes do not happen
in parallel with each other but in phases
```python
    def tx_create(self,
                  account,
                  amount=config.CONTRACT_DEFAULT_AMOUNT,
                  deposit=config.CONTRACT_DEFAULT_DEPOSIT,
                  init_state="()",
                  gas=config.CONTRACT_DEFAULT_GAS,
                  gas_price=config.CONTRACT_DEFAULT_GAS_PRICE,
                  fee=config.DEFAULT_FEE,
                  vm_version=config.CONTRACT_DEFAULT_VM_VERSION,
                  tx_ttl=config.DEFAULT_TX_TTL):
        """
        Create a contract and deploy it to the chain
        :return: address
        """
        try:
            call_data = self.encode_calldata("init", init_state)

            # get the transaction builder
            txb = self.client.tx_builder
            # get the account nonce and ttl
            nonce, ttl = self.client._get_nonce_ttl(account.get_address(), tx_ttl)
            # build the transaction
            tx, contract_id = txb.tx_contract_create(account.get_address(), self.bytecode, call_data, amount, deposit, gas, gas_price, vm_version,
                                                     fee, ttl, nonce)
            # sign the transaction
            tx_signed, sg, tx_hash = self.client.sign_transaction(account, tx)
            # post the transaction to the chain
            self.client.broadcast_transaction(tx_signed, tx_hash)
            # store the contract address in the instance variabl
            self.address = contract_id
            return tx, tx_signed, sg, tx_hash
        except OpenAPIClientException as e:
            raise ContractError(e)
```
This is the compiling function that generates a Sophia smart contract from
the source code. The parameters to keep in mind in this function are.
- Parameter Code: The source code of the contracts
- Parameter Options: Additional options for the contract.

The ```compile``` function should return the contracts bytecode.
```python
    def compile(self, code, options=''):
        """
        Compile a sophia contract from source
        :param code: the source code of the the contract
        :param options: additional options for the contract TODO: link the documentation for the options
        :return: the contract bytecode
        """
        try:
            data = self.client.compile_contract(body=dict(
                code=code,
                options=options
            ))
            return data.bytecode
        except OpenAPIClientException as e:
            raise ContractError(e)

    def get_pretty_bytecode(self, code, options=''):
        return pretty_bytecode(self.bytecode)
```
The call function has a pre-defined name and argument in the given bytecode that exists off chain.
The data is created and the contract is called. Meaning it allows you to interact with contracts that exist already on chain.
Another function example is to query the node to find out whether what will happen if you do call a specific smart contract(the Query contract nodes feature is not currently functional in the python SDK)

```python
    def call(self, function, arg):
        '''"Call a sophia function with a given name and argument in the given
        bytecode off chain.'''
        try:
            # see: /epoch/lib/aehttp-0.1.0/src/aehttp_dispatch_ext.erl
            data = self.client.call_contract(body=dict(
                code=self.bytecode,
                function=function,
                arg=arg,
                abi=self.abi,
            ))
            return data
        except OpenAPIClientException as e:
            raise ContractError(e)
```

The encode function and arguments of a contract call allows for the contract to be encoded onto the chain.

```python
    def encode_calldata(self, function, arg):
        """
        Encode the function and arguments of a contract call.
        """
        try:
            data = self.client.encode_calldata(body=dict(
                abi=self.abi,
                code=self.bytecode,
                function=function,
                arg=arg,
            ))
            return data.calldata
        except OpenAPIClientException as e:
            raise ContractError(e)
```
The decode_data function decodes the data on the contract computation. The parameters to pay attention too inlude:

Parameter ```Data```: The result returned by a contract execution
Parameter ```Sophia_type```: The expected type of the result.

The decoded data will return a Tuple, The tuples value and type is immutable.

```python
    def decode_data(self, data, sophia_type):
        """
        Decode the result of a contract computation
        :param data: the result returned by a contract execution
        :param sophia_type: the expected type of the result

        :return: a tuple of (value, type)
        """
        try:
            reply = self.client.decode_data(body={
                "data": data,
                "sophia-type": sophia_type,
            })
            return reply.data.get('value'), reply.data.get('type', 'word')
        except OpenAPIClientException as e:
            raise ContractError(e)
```
