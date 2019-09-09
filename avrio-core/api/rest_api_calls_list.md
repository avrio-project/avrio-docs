Avrio Core rest api
==============================

The rest api runs on the defult json rpc port.

API call list
-------------

#### Transactions
`GET /rest/tx/<TX-HASH>`

Given a transaction hash: returns a transaction in JSON format.

NOTE: this will only search the mempool.
To query for a confirmed transaction use the json rpc command.

#### Blocks
`GET /rest/block/<BLOCK-HASH>.<bin|hex|json>`
`GET /rest/block/notxdetails/<BLOCK-HASH>`

Given a block hash: returns a block, in JSON format.
Responds with 404 if the block doesn't exist.

The HTTP request and response are both handled entirely in-memory, thus making maximum memory usage at least 2.66MB (1 MB max block, plus hex encoding) per request.

With the /notxdetails/ option JSON response will only contain the transaction hash instead of the complete transaction details. The option only affects the JSON response.

#### Blockheaders
`GET /rest/headers/<COUNT>/<BLOCK-HASH>`

Given a block hash: returns <COUNT> number of blockheaders in upward direction.
Returns empty if the block doesn't exist or it isn't in the active chain.

#### Blockhash by height
`GET /rest/blockhashbyheight/<HEIGHT>`

Given a height: returns hash of block in best-block-chain at height provided.

#### Chaininfos
`GET /rest/chaininfo/<CHAINKEY>`

Returns various state info regarding CHAINKEY blockchain's processing.
Only supports JSON as output format.
* chain : (string) the public key of the chain
* blocks : (numeric) the current number of blocks processed in the server
* headers : (numeric) the current number of headers we have validated
* topblockhash : (string) the hash of the top block
* verificationprogress : (numeric) estimate of verification progress [0..1]
* merkleroot : (strng) a merkle root of the chain

#### get account balance
`GET /rest/getbalance/<account>`
`GET /rest/getbalancelist/[COUNT]`
The getbalance command allows querying of the balance of a account, getbalance list returns top COUNT balances from the list of balances in json format (publickkey : balance)
Example:
```
$ curl localhost:port/rest/getbalance/b2cdfd7b89def827ff8af7cd9bff7627ff72e5e8b0f71210f92ea7a4000c5d75 | json_pp
{
   "publicKey" : "b2cdfd7b89def827ff8af7cd9bff7627ff72e5e8b0f71210f92ea7a4000c5d75",
   "balance" : 2485.53,
}
```

#### Memory pool
`GET /rest/mempool/info.json`

Returns various information about the TX mempool.
Only supports JSON as output format.
* loaded : (boolean) if the mempool is fully loaded
* size : (numeric) the number of transactions in the TX mempool
* bytes : (numeric) size of the TX mempool in bytes
* usage : (numeric) total TX mempool memory usage
* maxmempool : (numeric) maximum memory usage for the mempool in bytes
* mempoolmingas : (numeric) minimum feerate (in gas) for tx to be accepted

`GET /rest/mempool/contents.json`

Returns pending (confirmed but waitng for a recive block) transactions in the TX mempool.
Only supports JSON as output format.

Contributers
-------------
EDITED FROM: github rest api docs (https://github.com/bitcoin/bitcoin/blob/master/doc/REST-interface.md)
