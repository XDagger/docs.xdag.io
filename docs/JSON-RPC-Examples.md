# JSON-RPC Examples

## Python

```
import requests
import json

url = 'http://127.0.0.1:7667' # The RPC server url
body = {"method":"xdag_state", "params":[], "id":1}
resp = requests.post(url, data = json.dumps(body))
print(resp.text)
```


## NodeJS

```
var request = require('request');

url = 'http://127.0.0.1:7667'; // The RPC server url
postData = {"method":"xdag_state", "params":[], "id":1};
 
request({
    url: url,
    method: "POST",
    json: true,
    headers: {
        "content-type": "application/json",
    },
    body: postData
}, function(error, response, body) {
    if (!error && response.statusCode == 200) {
        console.log(body);
    }
});
```