# Trade History

Get user trade history.

### Sample Request \(Python\)

```py
import requests

url = "https://openapi.bitmart.com/v2/trades?symbol=BMX_ETH&limit=10&offset=0"

// timestamp is in milliseconds and the authorization header is "Bearer " + token
headers = {"X-BM-TIMESTAMP": xxx, "X-BM-AUTHORIZATION": "xxx"}

response = requests.get(url, headers=headers)

print(response.text)
```

### Sample Request \(Go\)
```go
func main() {
	access_token := get_access_token(api_key, api_secret, memo)

	URL := endpoint + "/v2/trades?symbol=BMX_ETH&limit=10&offset=0"

	req, _ := http.NewRequest("GET", URL, nil)

	req.Header.Add("X-Bm-Timestamp", fmt.Sprintf("%d", time.Now().UnixNano()/1000000))
	req.Header.Add("X-Bm-Authorization", "Bearer "+access_token)

	res, err := http.DefaultClient.Do(req)
	if err != nil {
		panic(err)
	}
	defer res.Body.Close()

	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(string(body))
}
```

### Sample Response

```js
{
    "total_trades": 216,
    "total_pages": 22,
    "current_page": 0,
    "trades": [
        {
            "symbol": "BMX_ETH",
            "amount": "1.0",
            "fees": "0.0005000000",
            "trade_id": 2734956,
            "price": "0.00013737",
            "active": true,
            "entrust_id": 5576623,
            "timestamp": 1545292334000
        },
        {
            "symbol": "BMX_ETH",
            "amount": "100.0",
            "fees": "0.0500000000",
            "trade_id": 2664776,
            "price": "0.00013472",
            "active": true,
            "entrust_id": 5389422,
            "timestamp": 1543964304000
        },
        {
            "symbol": "BMX_ETH",
            "amount": "1.0",
            "fees": "0.0005000000",
            "trade_id": 1710378,
            "price": "0.00010767",
            "active": true,
            "entrust_id": 4237941,
            "timestamp": 1537956889000
        },
        {
            "symbol": "BMX_ETH",
            "amount": "1.0",
            "fees": "0.0005000000",
            "trade_id": 1710376,
            "price": "0.00010767",
            "active": true,
            "entrust_id": 4237940,
            "timestamp": 1537956889000
        },
        {
            "symbol": "BMX_ETH",
            "amount": "1.0",
            "fees": "0.0005000000",
            "trade_id": 1710374,
            "price": "0.00010767",
            "active": true,
            "entrust_id": 4237939,
            "timestamp": 1537956887000
        },
        {
            "symbol": "BMX_ETH",
            "amount": "1.0",
            "fees": "0.0005000000",
            "trade_id": 437647,
            "price": "0.00010300",
            "active": true,
            "entrust_id": 563191,
            "timestamp": 1535372305000
        },
        {
            "symbol": "BMX_ETH",
            "amount": "388.0",
            "fees": "0.1940000000",
            "trade_id": 337439,
            "price": "0.00009000",
            "active": true,
            "entrust_id": 475766,
            "timestamp": 1534801638000
        },
        {
            "symbol": "BMX_ETH",
            "amount": "2162.0",
            "fees": "1.0810000000",
            "trade_id": 337437,
            "price": "0.00009000",
            "active": true,
            "entrust_id": 475766,
            "timestamp": 1534801637000
        },
        {
            "symbol": "BMX_ETH",
            "amount": "2037.0",
            "fees": "1.0185000000",
            "trade_id": 337435,
            "price": "0.00009000",
            "active": true,
            "entrust_id": 475766,
            "timestamp": 1534801636000
        },
        {
            "symbol": "BMX_ETH",
            "amount": "1385.0",
            "fees": "0.6925000000",
            "trade_id": 337433,
            "price": "0.00009000",
            "active": true,
            "entrust_id": 475766,
            "timestamp": 1534801634000
        }
    ]
}
```

#### Request Parameter

| Parameter | Type | Description |
| :--- | :--- | :--- |
| symbol | query | Trading pair symbol |
| entrust_id | query | Order id when placed |
| offset | query | Current page, which starts from 0 |
| limit | query | Maximum size of the results in one page (default 500, maximum 1000) |

#### Polling

```offset``` and ```limit``` are optional. If they are not passed in, the result contains all orders that satisfy ```symbol``` and ```status``` restrictions.

```entrust_id``` is optional too. However, if ```entrust_id``` is passed in, ```offset``` and ```limit``` will have no effect.

#### Response Details

| Key | Type | Description |
| :--- | :--- | :--- |
| trades | array | List of orders |
| entrust_id | string | Order id |
| trade_id | string | Trade history id |
| symbol | string | Trading pair symbol |
| timestamp | string | Execution time (in milliseconds) |
| active | boolean | Order status |
| price | string | Executed price |
| fees | string | Executed fee |
| amount | string | Executed amount |
| total_pages | string | Total number of pages |
| total_trades | string | Total number of trades |
| current_page | string | Current page number |




