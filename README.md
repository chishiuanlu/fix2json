fix2json
=====

## About 

fix2json is a command-line utility to present FIX(TV) protocol message files as JSON.

Some scenarios where fix2json might be of use are:

* Within the ingestion pipeline of trading venue drop copy files into ElasticSearch

* Performing command-line ETL or manipulation of FIX data, often in concert with other CLI utilities such as jq or XMLStarlet

* As a pre-processor for inserting FIX records into JSON-conformant NoSQL repositories, such as Google BigQuery or MongoDB. 

The current level of fix2json semantic naivete is very high.  As such, users should consider ensuring the semantic validity of all FIX messages upstream.

## Install

```bash
npm install -g fix2json
```
## Examples
```bash
$ ./fix2json.js
Usage: fix2json [-p] <data dictionary xml file> [<path to FIX message file>]

$ du -hs MDFF_CME_20130714-20130715_7818_0
2.2G      MDFF_CME_20130714-20130715_7818_0

$ ./fix2json.js dict/FIX50SP2.xml MDFF_CME_20130714-20130715_7818_0 
{"BodyLength":"3972","CheckSum":"117","SecurityIDSource":"EXCHANGE SYMBOL","MsgSeqNum":"1950185","MsgType":"MARKETDATAINCREMENTALREFRESH","SecurityID":"100696","SenderCompID":"CME","SendingTime":"20130715164359550","TradeDate":"20130715","RptSeq":"1603","SecurityDesc":"ESV3 P1220","NoMDEntries":"39","MDEntryType":"BID","MDEntryPx":"80","MDEntrySize":"980","MDEntryTime":"164359000","MDUpdateAction":"CHANGE","TradingSessionID":"HALFDAY","NumberOfOrders":"4","MDPriceLevel":"3","ApplVerID":"FIX50SP2"}
{"BodyLength":"102","CheckSum":"001","SecurityIDSource":"EXCHANGE SYMBOL","MsgSeqNum":"17554","MsgType":"SECURITYSTATUS","SecurityID":"102149","SenderCompID":"CME","SendingTime":"20130714180212729","TradeDate":"20130715","SecurityDesc":"ESZ3 C2050","HighPx":"9999900","LowPx":"5","ApplVerID":"FIX50SP2"}
{"BodyLength":"5733","CheckSum":"062","SecurityIDSource":"EXCHANGE SYMBOL","MsgSeqNum":"1041351","MsgType":"MARKETDATAINCREMENTALREFRESH","SecurityID":"103998","SenderCompID":"CME","SendingTime":"20130715141815962","TradeDate":"20130715","RptSeq":"7443","SecurityDesc":"ESZ3 P1760","NoMDEntries":"57","MDEntryType":"OFFER","MDEntryPx":"11975","MDEntrySize":"25","MDEntryTime":"141815000","MDUpdateAction":"DELETE","TradingSessionID":"HALFDAY","NumberOfOrders":"1","MDPriceLevel":"2","ApplVerID":"FIX50SP2"}
{"BodyLength":"4343","CheckSum":"005","SecurityIDSource":"EXCHANGE SYMBOL","MsgSeqNum":"2690379","MsgType":"MARKETDATAINCREMENTALREFRESH","SecurityID":"117457","SenderCompID":"CME","SendingTime":"20130715193111628","TradeDate":"20130715","RptSeq":"543","SecurityDesc":"ESN3 C2125","NoMDEntries":"43","MDEntryType":"OFFER","MDEntryPx":"35","MDEntrySize":"325","MDEntryTime":"193111000","MDUpdateAction":"NEW","TradingSessionID":"HALFDAY","NumberOfOrders":"2","MDPriceLevel":"3","ApplVerID":"FIX50SP2"}
{"BodyLength":"140","CheckSum":"193","SecurityIDSource":"EXCHANGE SYMBOL","MsgSeqNum":"17557","MsgType":"MARKETDATAINCREMENTALREFRESH","SecurityID":"102143","SenderCompID":"CME","SendingTime":"20130714180212777","SettlDate":"20130712","TradeDate":"20130715","RptSeq":"1","SecurityDesc":"ESZ3 P0850","NoMDEntries":"1","MDEntryType":"SETTLEMENT PRICE","MDEntryPx":"30","MDEntryTime":"180212000","MDUpdateAction":"NEW","ApplVerID":"FIX50SP2"}
{"BodyLength":"143","CheckSum":"122","SecurityIDSource":"EXCHANGE SYMBOL","MsgSeqNum":"19979","MsgType":"MARKETDATAINCREMENTALREFRESH","SecurityID":"105756","SenderCompID":"CME","SendingTime":"20130714180226470","SettlDate":"20130712","TradeDate":"20130715","RptSeq":"1","SecurityDesc":"ESZ3 P1745","NoMDEntries":"1","MDEntryType":"SETTLEMENT PRICE","MDEntryPx":"10850","MDEntryTime":"180226000","MDUpdateAction":"NEW","ApplVerID":"FIX50SP2"}
...

$ ./fix2json.js -p dict/FIX50SP2.xml MDFF_CME_20130714-20130715_7818_0 
{
    "BodyLength": "3972",
    "CheckSum": "117",
    "SecurityIDSource": "EXCHANGE SYMBOL",
    "MsgSeqNum": "1950185",
    "MsgType": "MARKETDATAINCREMENTALREFRESH",
    "SecurityID": "100696",
    "SenderCompID": "CME",
    "SendingTime": "20130715164359550",
    "TradeDate": "20130715",
    "RptSeq": "1603",
    "SecurityDesc": "ESV3 P1220",
    "NoMDEntries": "39",
    "MDEntryType": "BID",
    "MDEntryPx": "80",
    "MDEntrySize": "980",
    "MDEntryTime": "164359000",
    "MDUpdateAction": "CHANGE",
    "TradingSessionID": "HALFDAY",
    "NumberOfOrders": "4",
    "MDPriceLevel": "3",
    "ApplVerID": "FIX50SP2"
}
{
    "BodyLength": "102",
    "CheckSum": "001",
    "SecurityIDSource": "EXCHANGE SYMBOL",
    "MsgSeqNum": "17554",
    "MsgType": "SECURITYSTATUS",
    "SecurityID": "102149",
    "SenderCompID": "CME",
    "SendingTime": "20130714180212729",
    "TradeDate": "20130715",
    "SecurityDesc": "ESZ3 C2050",
    "HighPx": "9999900",
    "LowPx": "5",
    "ApplVerID": "FIX50SP2"
}
{
    "BodyLength": "5733",
    "CheckSum": "062",
    "SecurityIDSource": "EXCHANGE SYMBOL",
    "MsgSeqNum": "1041351",
    "MsgType": "MARKETDATAINCREMENTALREFRESH",
    "SecurityID": "103998",
    "SenderCompID": "CME",
    "SendingTime": "20130715141815962",
    "TradeDate": "20130715",
    "RptSeq": "7443",
    "SecurityDesc": "ESZ3 P1760",
    "NoMDEntries": "57",
    "MDEntryType": "OFFER",
    "MDEntryPx": "11975",
    "MDEntrySize": "25",
    "MDEntryTime": "141815000",
    "MDUpdateAction": "DELETE",
    "TradingSessionID": "HALFDAY",
    "NumberOfOrders": "1",
    "MDPriceLevel": "2",
    "ApplVerID": "FIX50SP2"
}
{
    "BodyLength": "4343",
    "CheckSum": "005",
    "SecurityIDSource": "EXCHANGE SYMBOL",
    "MsgSeqNum": "2690379",
    "MsgType": "MARKETDATAINCREMENTALREFRESH",
    "SecurityID": "117457",
    "SenderCompID": "CME",
    "SendingTime": "20130715193111628",
    "TradeDate": "20130715",
    "RptSeq": "543",
    "SecurityDesc": "ESN3 C2125",
    "NoMDEntries": "43",
    "MDEntryType": "OFFER",
    "MDEntryPx": "35",
    "MDEntrySize": "325",
    "MDEntryTime": "193111000",
    "MDUpdateAction": "NEW",
    "TradingSessionID": "HALFDAY",
    "NumberOfOrders": "2",
    "MDPriceLevel": "3",
    "ApplVerID": "FIX50SP2"
}
{
    "BodyLength": "140",
    "CheckSum": "193",
    "SecurityIDSource": "EXCHANGE SYMBOL",
    "MsgSeqNum": "17557",
    "MsgType": "MARKETDATAINCREMENTALREFRESH",
    "SecurityID": "102143",
    "SenderCompID": "CME",
    "SendingTime": "20130714180212777",
    "SettlDate": "20130712",
    "TradeDate": "20130715",
    "RptSeq": "1",
    "SecurityDesc": "ESZ3 P0850",
    "NoMDEntries": "1",
    "MDEntryType": "SETTLEMENT PRICE",
    "MDEntryPx": "30",
...

$ fix2json dict/FIX42.xml fixmsg_11212014.txt | mongoimport --drop --collection FIX
connected to: 127.0.0.1
2015-08-20T15:19:21.465-0400 dropping: test.FIX
2015-08-20T15:19:24.013-0400     		15600	5200/second
2015-08-20T15:19:27.000-0400 			34600	5766/second
2015-08-20T15:19:30.005-0400 			53400	5933/second
2015-08-20T15:19:33.009-0400 			72900	6075/second
2015-08-20T15:19:36.005-0400 			88500	5900/second
2015-08-20T15:19:39.010-0400 			108200	6011/second
2015-08-20T15:19:42.005-0400 			127300	6061/second
2015-08-20T15:19:45.001-0400 			146800	6116/second
2015-08-20T15:19:48.001-0400 			166000	6148/second
2015-08-20T15:19:51.429-0400 			183600	6120/second
2015-08-20T15:19:54.010-0400 			200200	6066/second
2015-08-20T15:19:55.980-0400 check 9 212993
2015-08-20T15:19:55.981-0400 imported 212993 objects


$ head -1 testfiles/100FIX42.dat | ./fix2json.js -p dict/FIX42.xml 
{
    "8201": "1",
    "Account": "909646300",
    "BeginString": "FIX.4.2",
    "BodyLength": "0",
    "CheckSum": "0",
    "ClOrdID": "0c968e69-c3ff-4f9f-bc66-9e5ebccd9807",
    "Currency": "USD",
    "IDSource": "CUSIP",
    "MsgSeqNum": "0",
    "MsgType": "ORDER SINGLE",
    "OrderQty": "75700",
    "OrdType": "MARKET",
    "OrigClOrdID": "e0568b5c-8bb1-41f0-97bf-5eed32828c24",
    "SecurityID": "464288430",
    "SenderCompID": "830199",
    "SendingTime": "20150406-12:17:27",
    "Side": "BUY",
    "Symbol": "SJM",
    "TargetCompID": "AZKJ",
    "TargetSubID": "3620",
    "TimeInForce": "DAY",
    "TransactTime": "20150406-12:17:27",
    "SecurityExchange": "P"
}


```

## Caveats

* fix2json makes no semantic judgements about the FIX data being processed and blindly applies the specified data dictionary to the input FIX file.  Feedback from the community on an appropriate level of validation is welcomed.

* fix2json now uses streams instead of loading up the entire source file in one go.  This means that you can process a 2G+ file starting immediately.  What this also means is that fix2json no longer returns a proper JSON array as it's output.  Individual JSON objects will be output that correspond to the individual messages in the source file.  For this reason, pretty printing is disabled by default.  Use ```-p``` as the first argument to pretty print the output JSON.

* fix2json will replace underscores ('_') with spaces (' ') for all mnemonic tag descriptions found in the input data dictionary.  Hence, a description for EventType will be in the data dictionary as "LAST_ELIGIBLE_TRADE_DATE", but will be interpreted by fix2json as "LAST ELIGIBLE TRADE DATE"

## See Also

* [FIX Protocol](http://fixprotocol.org)
* [FixSpec.com Developer Tools](https://fixspec.com/developers)
* [FIX on Wikipedia](http://en.wikipedia.org/wiki/Financial_Information_eXchange)
* [json CLI](https://github.com/trentm/json)
* [jq CLI](https://github.com/stedolan/jq)

## License
MIT. See license text in [LICENSE](LICENSE).

## Copyrights and Names
Copyright © SunGard 2015. Licensed under the MIT license.   
