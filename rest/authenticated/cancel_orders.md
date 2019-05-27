# Cancel All Orders

Cancel orders for given condintions.

### Sample Request \(Python\)

```py
import requests

url = "https://openapi.bitmart.com/v2/orders?symbol=BMX_ETH&side=buy"

// timestamp is in milliseconds and the authorization header is "Bearer " + token
headers = {"X-BM-TIMESTAMP": xxx, "X-BM-AUTHORIZATION": "xxx"}

response = requests.delete(url, headers=headers)

print(response.text)
```

### Sample Request \(Go\)
```go
func main() {
	access_token := get_access_token(api_key, api_secret, memo)

	URL := endpoint + "/v2/orders?symbol=BMX_ETH&side=buy"

	req, _ := http.NewRequest("DELETE", URL, nil)

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
{}
```

#### Request Parameter

| Parameter | Type | Description |
| :--- | :--- | :--- |
| symbol | query | Trading pair symbol |
| side | query | 'buy' or 'sell' |







