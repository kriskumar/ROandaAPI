# ROandaAPI (Clone of oandar)

`oandar` package is a R wrapper for the [OANDA REST API](http://developer.oanda.com/rest-live/introduction/).
`ROandaAPI` is in developement and builds on `oandar` package ...

```

install.packages("devtools") # if you have not installed "devtools" package
devtools::install_github("kriskumar/ROandaAPI")

```
## Simple Example

First we get the accounts that exist

```
require(ROandaAPI)
atype<-"trade"
token<-"0000longtoken00000"
oanda<-generate_oanda(token,atype)
accounts(oanda)
```
Let us get some historical data 

```
require(tidyquant)
mktdata<-instrument_history(oanda,"EUR_USD","D",candle_format = "midpoint")
mktdata %>%
    ggplot(aes(x = time, y = close_bid)) +
    geom_barchart(aes(open = open_bid, high = high_bid, low = low_bid, close = close_bid)) +
    labs(title = "EURUSD Bar Chart", y = "Closing Price", x = "") + 
    theme_tq()
    
```

Now let us create an order

```
order<-create_order(oanda,"USD_SEK",100,"sell","market",account_id = xx8x8)
```