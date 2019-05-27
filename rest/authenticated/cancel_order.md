# Cancel an Order

Cancel a specific order.

### HMAC SHA256 signature

HMAC SHA256 signature will be used as the value of _**X-BM-SIGNATURE**_ header. We highly recommend to sign the payload in case the request body is hacked.

Here is a sample request from the Linux comman line using ```echo```, ```openssl``` and ```curl```.

| Key | Value |
| :--- | :--- |
| entrust_id | 1223181 |

```sh
[linux]$ echo -n "entrust_id=1223181" | openssl dgst -sha256 -hmac "8c08d9d5c3d15b105dbddaf96e427ac6"
(stdin)= de4ed768cea4eb2f0fe081009eab1f41c5fd6ff6ed53768df7fe252472c257b3
```

### Sample Request \(Python 2\)

```py
import requests
import hmac
import hashlib
from urllib import urlencode

entrust_id = ***
url = "https://openapi.bitmart.com/v2/orders/%s" % entrust_id

// timestamp is in milliseconds and the authorization header is "Bearer " + token
// X-BM-SIGNATURE is the HMAC SHA256 signature of the request parameters encrypted by API Secret

secret = "***"
headers = {"X-BM-TIMESTAMP": ***, "X-BM-AUTHORIZATION": "***"}

data = {"entrust_id": entrust_id}

// notice: the parameters should be sorted in alphabetical order
sorted_data = sorted(data.items(), key=lambda d: d[0], reverse=False)
message = str(urlencode(sorted_data))
signed_message = hmac.new(secret, message, hashlib.sha256).hexdigest()

// add signed_message to the headers
headers["X-BM-SIGNATURE"] = signed_message

response = requests.delete(url, headers=headers)

print(response.text)
```

### Sample Request \(Go\)
```go
func main() {
    entrust_id := "1223181"
    access_token := get_access_token(api_key, api_secret, memo)

    URL := endpoint + "/v2/orders/"
    URL += entrust_id

    message := fmt.Sprintf("entrust_id=%s", entrust_id)

    req, _ := http.NewRequest("DELETE", URL, nil)

    req.Header.Add("X-Bm-Timestamp", fmt.Sprintf("%d", time.Now().UnixNano()/1000000))
    req.Header.Add("X-Bm-Authorization", "Bearer "+access_token)
    req.Header.Add("X-Bm-Signature", create_sha256_signature(api_secret, message))

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
| entrust_id | path | Order id |







