# Ticker

The ticker is a high level overview of the state of the market. It shows you the current best bid and ask, as well as the last trade price. It also includes information such as daily volume and how much the price has moved over the past 24 hours.

### Sample Request \(Python\)

```py
import requests

url = "https://openapi.bitmart.com/v2/ticker?symbol=BMX_ETH"

response = requests.request("GET", url)

print(response.text)
```

### Sample Response

```js
{  
    "volume":"17603607.6",
    "ask_1":"0.00010030",
    "base_volume":"1765.0",
    "lowest_price":"0.00009900",
    "bid_1":"0.00009901",
    "highest_price":"0.00011000",
    "ask_1_amount":"211",
    "current_price":"0.00009944",
    "fluctuation":"-0.0058",
    "symbol_id":"BMX_ETH",
    "url":"https://www.bitmart.com/trade?symbol=BMX_ETH",
    "bid_1_amount":"95"
}
```

#### Request Parameter

| Parameter | Type | Description |
| :--- | :--- | :--- |
| symbol | query | Trading pair symbol (optional, if not passed in, return all products' ticker information) |

#### Response Details

| Key | Type | Description |
| :--- | :--- | :--- |
| symbol\_id | string | Trading pair symbol |
| volume | string | Trading volume |
| base\_volume | string | Target volume |
| highest\_price | string | Highest price within 24 hr |
| lowest\_price | string | Lowest price within 24 hr |
| current\_price | string | Current price |
| ask\_1 | string | Asked price |
| ask\_1\_amount | string | Asked amount
| bid\_1 | string | Bid price |
| bid\_1\_amount | string | Bid amount
| fluctuation | string | Price change within 24 hr |
| url | string | Trading url at bitmart.com |



