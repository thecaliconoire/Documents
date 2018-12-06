```python
import requests
```
Makes HTTPS url requests simpler. The requests library is under the apache2 license.

```python
import sys
```
The sys module gives access to variables used or maintained by the interpreter and to functions that interact with the systems interpreter.

```python
from collections import MutableSequence
```
The collections librarys MutableSequence dialog allows for characters, and floats to be changed after the sequence is created.

```python
from . import __compatibility__
```
import the compatibility module.

virtual machine version and specifications are found [here](https://github.com/aeternity/protocol/blob/master/contracts/contract_vms.md#virtual-machines-on-the-%C3%A6ternity-blockchain):

```python
AEVM_NO_VM = 0
```


For more information on the max number of blocks into the future that the name is going to be available for please read the [Protocol](https://github.com/aeternity/protocol/blob) on [AENS](https://github.com/aeternity/protocol/blob/epoch-v0.22.0/AENS.md#update) specifically [aens-entry](44a93d3aab957ca820183c3520b9daf6b0fedff4/AENS.md#aens-entry)


Time-To-Live is abbreviated too ```TTL```.  TTL is expressed as _n_ blocks from now. The program is set to have a max TTL of 36000 blocks from now.
```python
NAME_MAX_TLL = 36000
NAME_CLIENT_TTL = 60000
DEFAULT_NAME_TTL = 500
```

Default relative TTL in number of blocks. The Default TTL set for a transaction is 500 blocks from the transaction blocks genesis.

```python
MAX_TX_TTL = sys.maxsize
DEFAULT_TX_TTL = 500
```

The default fee for posting transaction

```python
DEFAULT_FEE = 10
```

The default gas amount, gas price, deposit, virtual machine version and the default amount needed to launch a contract on chain.

```python
CONTRACT_DEFAULT_GAS = 1000
CONTRACT_DEFAULT_GAS_PRICE = 1
CONTRACT_DEFAULT_DEPOSIT = 4
CONTRACT_DEFAULT_VM_VERSION = 1
CONTRACT_DEFAULT_AMOUNT = 1
```
Oracles
The default configuration for an Oracles initiation. Fee, Time-to-Live (TTL), default TTL types, values, how much it costs to query the Oracle, and the virtual machines version.
```python

https://github.com/aeternity/protocol/blob/master/oracles/oracles.md#technical-aspects-of-oracle-operations
ORACLE_DEFAULT_QUERY_FEE = 10
ORACLE_DEFAULT_TTL_TYPE_DELTA = 'delta'
ORACLE_DEFAULT_TTL_TYPE_BLOCK = 'block'
ORACLE_DEFAULT_TTL_VALUE = 500
ORACLE_DEFAULT_QUERY_TTL_VALUE = 100
ORACLE_DEFAULT_RESPONSE_TTL_VALUE = 100
ORACLE_DEFAULT_VM_VERSION = AEVM_NO_VM
```

The default network is set too the aemainet, however other networks such as the Testnet is available.

```python
DEFAULT_NETWORK_ID = "ae_mainnet"
@classmethod
@classmethod
```

Tuning the MAX_RETRIES is the number of exponential back off when checking a transaction with the polling interval occurring every 2 seconds.

```python
MAX_RETRIES = 7  # used in exponential backoff when checking a transaction
POLLING_INTERVAL = 2  # in seconds
```
An error will occur if the configuration is not set up too minimum specs.

```python
class ConfigException(Exception):
    pass
```
An error will occur if you are running an unsupported and depreciated version of epoch.

```python
class UnsupportedEpochVersion(Exception):
    pass
```
The python SDK config class allows for it to call default settings into other modules. The init method creates the object from the class. Self creates a new object within a class.

```python
class Config:
    default_configs = None

    def __init__(self,
                 external_url='http://localhost:3013',
                 internal_url='http://localhost:3113',
                 websocket_url=None,
                 force_compatibility=False,
                 network_id=DEFAULT_NETWORK_ID):

        # endpoint urls
        self.websocket_url = websocket_url
        self.api_url_internal = internal_url
        self.api_url = external_url
        # get the version
        self.name_url = f'{self.api_url}/name'
        self.pubkey = None
        self.network_id = network_id
        # retrieve the version of the node we are connecting to
        try:
            r = requests.get(f"{self.api_url}/v2/status").json()
            self.node_version = r.get('node_version', 'unknown')
            if self.node_version not in __compatibility__ and not force_compatibility:
                raise UnsupportedEpochVersion(f"Unsupported epoch version {self.node_version}, supported version are {', '.join(__compatibility__)}")
        except requests.exceptions.ConnectionError as e:
            raise ConfigException(f"Error connecting to the epoch node at {self.api_url}, connection unavailable")
        except Exception as e:
            raise UnsupportedEpochVersion(f"Unable to understand node reply, perhaps is not an epoch node or is too old?")
```
This sets the default configuration that will be used by the epoch client if it does not get a config, passed into its constructor, in this case the Epoch client will return none.
```python
    def __str__(self):
        return f'ws:{self.websocket_url} ext:{self.api_url} int:{self.api_url_internal}'

    @classmethod
    def set_defaults(cls, config):
        """
        sets the default configuration that will be used when the epoch client
        did not get a config passed into its constructor

        :return: None
        """
        if not isinstance(config, MutableSequence):
            config = [config]
        cls.default_configs = config
```
The @classmethod get_defaults returns the default config that was defined above. Or it will generate a configuration from the different environmental variables.

```python
    @classmethod
    def get_defaults(cls):
        """
        returns the previously set default config or constructs a configuration
        automatically from environment variables

        :return: Config
        """
        if cls.default_configs is None:
            cls.default_configs = [Config()]
        return cls.default_configs
```
