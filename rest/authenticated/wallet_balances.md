# Wallet Balances

Get user wallet balances.

### Sample Request \(Python\)

```py
import requests

url = "https://openapi.bitmart.com/v2/wallet"

// timestamp is in milliseconds and the authorization header is "Bearer " + token
headers = {"X-BM-TIMESTAMP": xxx, "X-BM-AUTHORIZATION": "Bearer xxxx-here-is-the-access-token"}

response = requests.get(url, headers=headers)

print(response.text)
```

### Sample Request \(Go\)
```go
func main() {
	access_token := get_access_token(api_key, api_secret, memo)

	URL := endpoint + "/v2/wallet"

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
[
   {
        "id": "BTC"
        "available": 10,
        "name": "Bitcoin",
        "frozen": 0,
    }, 
    
    ...
]
```

#### Response Details

| Key | Type | Description |
| :--- | :--- | :--- |
| id | string | This is the short name of the currency. |
| name | string | This is the full name of the currency. |
| available | string | This is the amount of available currency. |
| frozen | string | This is the amount of frozen currency. |


