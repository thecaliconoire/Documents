_Epoch_ is the reference implementation model for æternity. Epoch is implemented in Erlang. The SDKs allow for communication with the Epoch and are written in [__Javascript__](https://github.com/aeternity/aepp-sdk-js), [__Python__](https://github.com/aeternity/aepp-sdk-python) and [__GO__](https://github.com/aeternity/aepp-sdk-go).

# __Aeternity SDK Networks__

*__SDK-testnet:__*
Is designed for users who are using a released versions of our SDKs (github releases or npm/yarn default install). This network is designed to be best for software developers.

The testnet runs the following Aepps:
* Token Faucet
* Contract Editor
* Blockchain Explorer

*__SDK-edgenet:__*
Is designed for users developing the SDKs, and developers who need the latest features from the develop branch on github. This network is used primarily for development and can be reset without notification.
If you clone one of our repos from the default branch (develop) you will connect to edgenet automatically.

* Token Faucet

# __Mining AE Tokens__
Using docker is the easiest way to mine AE tokens. Please make sure that you have Docker [docker](https://www.docker.com) and have it running. Then install an image file. First, determine the version of Epoch is needed then by using the ```/v2/status``` endpoint.

You should see the following output:
```yaml
// 20181109160745
// https://sdk-edgenet.aepps.com/v2/status
{
  "difficulty": 2017450664,
  "genesis_key_block_hash": "kh_2D3fMvkjuNaDwsrTctR4DjWUzztys8b1NBQrQYedTgCvZSkGpJ",
  "listening": true,
  "node_revision": "765f9cc0fb0904adb4efd0acfecd3c78c0d570f3",
  "node_version": "0.25.0",
  "peer_count": 0,
  "pending_transactions_count": 0,
  "protocols": Array[1][
    {
      "effective_at_height": 0,
      "version": 28
    }
  ],
  "solutions": 0,
  "syncing": true
}
```
 Next identify the ```node_version```. This example indicates that the node version is 25.0. After you find the Node version create the config file for that version.

 Create a swagger file myepoch.yaml, the correct versions contents. For example if the ```node_version``` is v0.24.0 run:
```yaml
 ---
peers:
  - aenode://pp_HdcpgTX2C1aZ5sjGGysFEuup67K9XiFsWqSPJs4RahEcSyF7X@sync.sdk-testnet.aepps.com:3015
keys:
    password: "top secret"
    dir: ./keys
chain:
    persist: true
mining:
    autostart: true
    beneficiary: "ak_2iBPH7HUz3cSDVEUWiHg76MZJ6tZooVNBmmxcgVK6VV8KAE688"
    cuckoo:
         miner:
             executable: mean16s-generic
             extra_args: ""
             node_bits: 16
```
if in similar too the example above the ```node_version``` is v0.25.00 then input the following.
```yaml
---
peers:
  - aenode://pp_HdcpgTX2C1aZ5sjGGysFEuup67K9XiFsWqSPJs4RahEcSyF7X@sync.sdk-edgenet.aepps.com:3015
keys:
    peer_password: "top secret"
    dir: ./keys
chain:
    persist: true
mining:
    autostart: true
    beneficiary: "ak_2iBPH7HUz3cSDVEUWiHg76MZJ6tZooVNBmmxcgVK6VV8KAE688"
    cuckoo:
         miner:
             executable: mean16s-generic
             extra_args: ""
             node_bits: 16
```

be sure to change the ```beneficiary``` to your accounts public key otherwise you will be giving your AE tokens away to the above account. **There will be future versions be sure to input the correct .yaml code.**

Now you should be able to run the following commands in your console.

```
docker run \
    -p 3013:3013 \
    -v $PWD/myepoch.yaml:/home/epoch/myepoch.yaml \   
    -e EPOCH_CONFIG=/home/epoch/myepoch.yaml \
     aeternity/epoch:vXX.Y.Z
```

Be sure to change the ```-v $PWD``` to the ```.yaml``` file you created and make sure that the ```aeternity/epoch:v``` is set too your ```node_version``` and you are ready to mine. Your output should appear similar to the following:

```
15:17:29.362 [info] TX-pool sync requries getting 0 TXs
15:17:29.757 [info] TX-pool sync added 0 TXs
15:17:30.212 [info] TX-pool synchronization finished!
15:17:42.344 [info] Synced blocks 1 - 1
15:17:50.976 [info] Synced blocks 2 - 35
15:17:51.775 [info] Synced blocks 36 - 96
15:17:52.009 [info] Synced blocks 97 - 100
```
