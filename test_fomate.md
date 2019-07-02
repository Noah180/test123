## getblockcount

Returns the number of blocks in the longest blockchain.

**Result:**

    n (numeric) The current block count

**Examples:**
  

    >qtum-cli getblockcount 
    
    >curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getblockcount", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:3889/

#### test: 

    ./qtum-cli getblockcount
#### test result: 

    395049

## 2. getblockchaininfo 
Returns an object containing various state info regarding blockchain processing.
#### Result:
```
{
  "chain": "xxxx",              (string) current network name as defined in BIP70 (main, test, regtest)
  "blocks": xxxxxx,             (numeric) the current number of blocks processed in the server
  "headers": xxxxxx,            (numeric) the current number of headers we have validated
  "bestblockhash": "...",       (string) the hash of the currently best block
  "difficulty": xxxxxx,         (numeric) the current difficulty
  "mediantime": xxxxxx,         (numeric) median time for the current best block
  "verificationprogress": xxxx, (numeric) estimate of verification progress [0..1]
  "initialblockdownload": xxxx, (bool) (debug information) estimate of whether this node is in Initial Block Download mode.
  "chainwork": "xxxx"           (string) total amount of work in active chain, in hexadecimal
  "size_on_disk": xxxxxx,       (numeric) the estimated size of the block and undo files on disk
  "pruned": xx,                 (boolean) if the blocks are subject to pruning
  "pruneheight": xxxxxx,        (numeric) lowest-height complete block stored (only present if pruning is enabled)
  "automatic_pruning": xx,      (boolean) whether automatic pruning is enabled (only present if pruning is enabled)
  "prune_target_size": xxxxxx,  (numeric) the target size used by pruning (only present if automatic pruning is enabled)
  "softforks": [                (array) status of softforks in progress
     {
        "id": "xxxx",           (string) name of softfork
        "version": xx,          (numeric) block version
        "reject": {             (object) progress toward rejecting pre-softfork blocks
           "status": xx,        (boolean) true if threshold reached
        },
     }, ...
  ],
  "bip9_softforks": {           (object) status of BIP9 softforks in progress
     "xxxx" : {                 (string) name of the softfork
        "status": "xxxx",       (string) one of "defined", "started", "locked_in", "active", "failed"
        "bit": xx,              (numeric) the bit (0-28) in the block version field used to signal this softfork (only for "started" status)
        "startTime": xx,        (numeric) the minimum median time past of a block at which the bit gains its meaning
        "timeout": xx,          (numeric) the median time past of a block at which the deployment is considered failed if not yet locked in
        "since": xx,            (numeric) height of the first block to which the status applies
        "statistics": {         (object) numeric statistics about BIP9 signalling for a softfork (only for "started" status)
           "period": xx,        (numeric) the length in blocks of the BIP9 signalling period 
           "threshold": xx,     (numeric) the number of blocks with the version bit set required to activate the feature 
           "elapsed": xx,       (numeric) the number of blocks elapsed since the beginning of the current period 
           "count": xx,         (numeric) the number of blocks with the version bit set in the current period 
           "possible": xx       (boolean) returns false if there are not enough blocks left in this period to pass activation threshold 
        }
     }
  }
  "warnings" : "...",           (string) any network and blockchain warnings.
}
```
**test:** 

    ./qtum-cli getblockchaininfo

**test result:**
```
{
  "chain": "main",
  "blocks": 401574,
  "headers": 401574,
  "bestblockhash": "be4cb62080f36d2c3a45127e016460aca82ea1de17af4166ad9341d1a18e00cc",
  "difficulty": 1699339.658646735,
  "moneysupply": 101586296,
  "mediantime": 1562032592,
  "verificationprogress": 0.9999994694221126,
  "initialblockdownload": false,
  "chainwork": "000000000000000000000000000000000000000000000113f4c983f14834f842",
  "size_on_disk": 1939468044,
  "pruned": false,
  "softforks": [
    {
      "id": "bip34",
      "version": 2,
      "reject": {
        "status": true
      }
    },
    {
      "id": "bip66",
      "version": 3,
      "reject": {
        "status": true
      }
    },
    {
      "id": "bip65",
      "version": 4,
      "reject": {
        "status": true
      }
    }
  ],
  "bip9_softforks": {
    "csv": {
      "status": "active",
      "startTime": 0,
      "timeout": 999999999999,
      "since": 6048
    },
    "segwit": {
      "status": "active",
      "startTime": 0,
      "timeout": 999999999999,
      "since": 6048
    }
  },
  "warnings": ""
}
```
## getblockhash height     

Returns hash of block in best-block-chain at height provided.

**Arguments:**
```
1. height         (numeric, required) The height index
```
**Result:**   
```
"hash"         (string) The block hash  
```


**Examples:**

    >qtum-cli getblockhash 1000  
    
    >curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getblockhash", "params": [1000] }' -H 'content-type: text/plain;' http://127.0.0.1:3889/

**test example:**

    ./qtum-cli getblockhash 1
    
**test result:**

    0000d5dab5e76310ae640e9bcfa270c2eb23a1e5948bdf01fc7ed1f157110ab7

