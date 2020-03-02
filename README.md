# Nodes

{% api-method method="get" host="http://127.0.0.1:98765" path="/json\_rpc/balance/:chainKey" %}
{% api-method-summary %}
Get Balance
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get free cakes.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Chain Key Or Username" type="string" %}
The public key or username of the account
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authentication" type="string" required=true %}
The RPC key you set in your config  
Default is passw0rd
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Account balance successfully retrieved.
{% endapi-method-response-example-description %}

```
{    "chainkey": "0xab734nfe...335a",    "balance" : 3483535, "locked" : 34324 }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=302 %}
{% api-method-response-example-description %}
This response is returned if you parse a bad hex key
{% endapi-method-response-example-description %}

```
{ "error" : "Failed to parse key" }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Could not find a cake matching this query.
{% endapi-method-response-example-description %}

```
{    "error": "Could not find account with key" }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
Something bad happens in the node, check the logs
{% endapi-method-response-example-description %}

```
{ "error" : "Internal Server Error"
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://127.0.0.1:98765" path="/json\_rpc/status/" %}
{% api-method-summary %}
getNodeStatus
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authentication" type="string" required=true %}
The RPC key you set in your config  
Default is passw0rd
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned upon no errors
{% endapi-method-response-example-description %}

```
{
    "node" : "4aiur3jvjjgvrjn6gfjn...",
    "number" : 432,
    "ip" : "172.85.353.34",
    "port" : 12345,
    "chainsDigest" : "3456jsnfn56usfjnef...",
    "synced" : true,
    "type" : "full",
    "publicKey" : "0x945ljknf30488gu0348gh0iwnev...",
    "commitee" : "0xuhgr...",
    "lastEpochVote" : 78,
    "function" : "validator",
    "newestBlockHash" : "0xijfe78r...",
    "peerCount" : 27,
    "uptime" : 2345678,
    "oneprobation" : false,    
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
This happens if you pass an incorect authentication key or token
{% endapi-method-response-example-description %}

```
{ "error" : "Unauthorized"
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
Something bad has happened in the server, check the logs for more details
{% endapi-method-response-example-description %}

```
{ "error" : "internal server error" }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://127.0.0.1:98765" path="/json\_rpc/chainStatus/:chainKey" %}
{% api-method-summary %}
chainStatus
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="Chain Key or Username" type="string" required=false %}
The public key or username assosiated with this account.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authentication" type="string" required=true %}
The RPC key you set in your config  
Default is passw0rd
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

