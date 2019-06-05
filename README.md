# Introduction

Welcome to BitMart trader and developer documentation. These documents outline exchange functionality, market details, and APIs.

APIs are separated into two categories: trading and feed. Trading APIs require authentication and provide access to placing orders and other account information. Feed APIs provide market data and are public.

**By accessing the BitMart Market Data API, you agree to be bound by the** [**Market Data Terms of Use**](https://support.bitmart.com/hc/en-us/articles/115004890354-Terms-of-Use).



# Documentation

* [REST](REST.md)
* [WEBSOCKET](WEBSOCKET.md)


# Legal

All APIs are used at your risk and expense. We are not responsible for any negligence, error, compromised security, malfunction, cyberattack, or other force majeure affecting this environment. You hereby release us, hold us harmless, and indemnify us from any and all damages, losses, or claims associated with your use of this environment.

# Contact

Join our [Telegram API Group](https://t.me/bitmart_api) and reach out to `Terence Lee`.

# Q&A

**Q: Can we use multiple valid token at the same time?**

A: Yes you may request multiple token and use at the same time. However, placing (or canceling) orders with multiple token at the same time is not allowed.

**Q: Do I need to request token every time before I make a functional call?**

A: No you don't have to because the token expiration time is 900 seconds which means you can get a token and use this token to make functional calls until the token expires. However, if you are trying to request token above rate limit (5 times per minute), you will get error back.

**Q: What is the limit rate of the REST api?**

A: The limit rate for token access is 5 times per minute, and the limit rate for other RESTful api is at most 1000s per second, and the api access is IP sensitive.

**Q: Is there any other limit for the api?**

A: Yes, our backend will evaluate user's trading behavior against the average user. The api abuse users will be banned from 1 day to 7 days.

The evaluation is based on:

- Repeatedly "one up" or "front-run" the best Bid/Ask on the Order Book
- Spam order creation and cancellation very quickly without executing trades
- Low (num of Trades / num of total orders) rate, that means the cancelled orders without execution rate is far bigger than the normal user
- BMX related pairs will be amplified judged.

# Release Notes

## 2019-02-14

* ```X-BM-SIGNATURE``` is mandatory for placing and canceling order.
* [Trade history](rest/authenticated/trade_history.md) API is added so user can track the execution history.
* ```precision``` parameter under [Order Book](rest/public/order_book.md) API is optional.
* ```symbol_id``` is added in [Ticker](rest/public/ticker.md) API.
* Improved trading efficiency.