---
id: rpc-api
title: JSON RPC API
---

# JSON-RPC API v0.1

[JSON](http://json.org/) is a lightweight data-interchange format. It can represent numbers, strings, ordered sequences of values, and collections of name/value pairs.

[JSON-RPC](http://www.jsonrpc.org/specification) is a stateless, light-weight remote procedure call (RPC) protocol. Primarily this specification defines several data structures and the rules around their processing. It is transport agnostic in that the concepts can be used within the same process, over sockets, over HTTP, or in many various message passing environments. It uses JSON ([RFC 4627](http://www.ietf.org/rfc/rfc4627.txt)) as data format.

XDAG provides experimental HTTP JSON-RPC for other trusted application to interact with xdag node.

## Curl Examples Explained

The curl options below might return a response where the node complains about the content type, this is because the --data option sets the content type to application/x-www-form-urlencoded . If your node does complain, manually set the header by placing -H "Content-Type: application/json" at the start of the call.

The examples also do not include the URL/IP & port combination which must be the last argument given to curl e.x. 127.0.0.1:7667

## Other Examples
* [JSON-RPC Examples](https://github.com/XDagger/xdag/wiki/JSON-RPC-Examples)  

## JSON-RPC methods
* [xdag_version](#xdag_version) 
* [xdag_get_account](#xdag_get_account)  
* [xdag_get_balance](#xdag_get_balance)  
* [xdag_state](#xdag_state)  
* [xdag_stats](#xdag_stats)  
* [xdag_get_block_info](#xdag_get_block_info) ***ONLY AVAILABLE FOR POOL***   
* [xdag_get_transactions](#xdag_get_transactions) ***ONLY AVAILABLE FOR POOL***   
* [xdag_do_xfer](#xdag_do_xfer)  
 

## JSON RPC API Reference

### xdag_version  

Return the xdag node version.

#### Parameter
NA

#### Returns
```[{"version":VERSION}]```

#### Example
```
// Request
curl -X POST --data '{"method":"xdag_version", "params":[], "id":1}'

// Result
{
	"result" : [
		{
			"version" : "0.2.1"
		}],
	"error" : null, 
	"id" : 1
}
```

### xdag_get_account  

Return the account information.

#### Parameter
1. ```DATA``` The number of account to be listed. Default is 20. [Optional]

#### Returns
```[{"address":ADDRESS, "balance":BALANCE, "key":KEY}]```

#### Example
```
// Request
curl -X POST --data '{"method":"xdag_get_account", "params":["20"], "id":1}'

// Result
{
	"result" : [
		{
			"address" : "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA",
			"balance" : "100000.00001",
			"key" : "0"
		},
		{
			"address" : "BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB",
			"balance" : "200000.00001",
			"key" : "0"
		}],
	"error" : null, 
	"id" : 1
}
```

### xdag_get_balance  

Return the balance of specified account

#### Parameter
1. ```DATA``` The specified account address. Default is current address. [Optional]

#### Returns
```[{"balance":"BALANCE"}]```

#### Example
```
// Request
curl -X POST --data '{"method":"xdag_get_balance", "params":["AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"], "id":1}'

// Response

{
	"result" : [{
			"balance" : "100000.00001"
		}],
	"error" : null, 
	"id" : 1
}
```


### xdag_state  

Return current state of connected node.

#### Parameter
none

#### Returns  
```["state":"CURRENT STATE"]```

#### Example

```
// Request
curl -X POST --data '{"method":"xdag_state", "params":[], "id":1}'

// Result
{
	"result" : ["current state"],
	"error" : null, 
	"id" : 1
}
```


### xdag_stats 
Return current stats of connected node.

#### Parameter
none

#### Returns  
```
[
    {
      "hashrate": "HASH RATE",
      "totalhashrate": "TOTAL HASH RATE",
      "hosts": "HOSTS",
      "totalhosts": "TOTAL HOSTS",
      "blocks": "BLOCKS",
      "totalblocks": "TOTAL BLOCKS",
      "mainblocks": "MAIN BLOCKS",
      "totalmainblocks": "TOTAL MAIN BLOCKS",
      "orphanblocks": "ORPHAN BLOCKS",
      "waitsyncblocks": "WAIT SYNC BLOCKS",
      "difficulty": "DIFFICULTY",
      "maxdifficulty": "MAX DIFFICULTY",
      "supply": "SUPPLY",
      "totalsupply": "TOTAL SUPPLY"
    }
  ]
```
  
#### Example

```
// Request
curl -X POST --data '{"method":"xdag_stats", "params":[], "id":1}'

// Result
{
  "result": [
    {
      "hashrate": "HASH RATE",
      "totalhashrate": "TOTAL HASH RATE",
      "hosts": "HOSTS",
      "totalhosts": "TOTAL HOSTS",
      "blocks": "BLOCKS",
      "totalblocks": "TOTAL BLOCKS",
      "mainblocks": "MAIN BLOCKS",
      "totalmainblocks": "TOTAL MAIN BLOCKS",
      "orphanblocks": "ORPHAN BLOCKS",
      "waitsyncblocks": "WAIT SYNC BLOCKS",
      "difficulty": "DIFFICULTY",
      "maxdifficulty": "MAX DIFFICULTY",
      "supply": "SUPPLY",
      "totalsupply": "TOTAL SUPPLY"
    }
  ],
  "error": null,
  "id": 1
}

```

### xdag_get_block_info    

Return the block information.

#### Parameter
1. ```ADDRESS``` The address or hash of the block to be listed.

#### Returns
```
[{"address":"ADDRESS","amount":"AMOUNT","flags":"BLOCK FLAGS","state":"BLOCK STATE","remark":"TRANSACTION REMARK","timestamp":"UTC TIMESTAMP","transactions":[{"address":"ADDRESS","amount":"AMOUNT","direction":"DIRECTION"}]}]
```

#### Example  
```
// Request
curl -X POST --data '{"method":"xdag_get_block_info", "params":["ADDRESS"], "id":1}'

// Result
{
	"result": [{
		"address": "BLOCK ADDRESS",
		"amount": "BLOCK AMOUNT",
		"flags": "BLOCK FLAGS",
		"state": "BLOCK STATE",
		"file pos": "POSITION OF BLOCK IN STORAGE FILE",
		"file": "PATH OF THE RELATED STORAGE FILE",
		"remark": "TRANSACTION REMARK",
		"timestamp": "2018-06-03 03:36:33.866 UTC",
		"transactions": [{ 
			"address": "ADDRESS",
			"amount": "10.111111",
			"direction": "input",
		}]
	}],
	"id": 1
}

```

### xdag_get_transactions  
Get transactions of specified address.

#### Parameter  
1. ```[{"address":"TO ADDRESS", "page":PAGE INDEX, "pagesize":PAGE SIZE}]```

#### Returns  
```
{["total":TOTAL_COUNT, "transactions":[{"state":"BLOCK STATE", "direction":"DIRECTION", "address":"ADDRESS", "amount":"AMOUNT", "timestamp":"UTC TIMESTAMP", "remark":"TRANSACTION REMARK"}]}
```

#### Example  
```
// Request
curl -X POST --data '{"method":"xdag_get_transactions", "params":[{"address":"ADDRESS", "page":0, "pagesize":50}], "id":1}'

// Result
{
	"result" : {
		"total":1,
		"transactions":[{ 
			"state": "BLOCK STATE",
			"direction": "input",
			"address": "ADDRESS",
			"amount": "10.111111",
			"timestamp": "2018-06-03 03:36:33.866 UTC",
 			"remark": "TRANSACTION REMARK"
		}]
	},
	"id" : 1
}

```

### xdag_do_xfer  
Do transaction to specified address. **Currently xdag_do_xfer is disabled by default, and can be enabled by pool owner through XDAG command line**

#### Parameter  
1. ```[{"amount":"AMOUNT", "address":"TO ADDRESS", "remark":"REMARK"}]```

#### Returns  
```[{"block":"TRANSACTION BLOCK ADDRESS"}]```

#### Example  
```
// Request
curl -X POST --data '{"method":"xdag_do_xfer", "params":[{"amount":"0.1", "address":"FQglVQtb60vQv2DOWEUL7yh3smtj7g1s", "remark":"REMARK"}], "id":1}'

// Result
{
	"result" : [{
		"block" : "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
	}],
	"error" : null, 
	"id" : 1
}

```