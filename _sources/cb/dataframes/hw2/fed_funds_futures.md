# Dataframe: `hw2:fed_funds_futures` - 30-Day Fed Funds Futures

Daily open, high, low, close and volume for the ZQ futures family, pilled from GLBX.MDP3 using the ohlcv-1d schema and parent symbol ZQ.FUT. Filter out spread symbols beofre using outright contracts. The implied monthly average rate in percent is 100 minus the future price.


## DataFrame Glimpse

```
Rows: 11862
Columns: 7
$ date   <datetime[ns]> 2026-10-23 00:00:00
$ symbol          <str> 'ZQZ6'
$ open            <f64> 95.965
$ high            <f64> 95.965
$ low             <f64> 95.945
$ close           <f64> 95.965
$ volume          <u64> 12677


```

## Dataframe Manifest

| Dataframe Name                 | 30-Day Fed Funds Futures                                                          |
|--------------------------------|--------------------------------------------------------------------------------------|
| Dataframe ID                   | [fed_funds_futures](../dataframes/hw2/fed_funds_futures.md)                                       |
| Sources                        | CME Globex                                          |
| Providers                      | Databento                                        |
| Provider Links                 | https://databento.com                                   |
| Tags                           | Fed Funds, Futures, Monetary Policy                                             |
| Access Types                   |                                       |
| How is data pulled?            | Databento Historical API via Python                                                   |
| Data available up to (min)     | 2026-10-23 00:00:00                                                             |
| Data available up to (max)     | 2026-10-23 00:00:00                                                             |
| Dataframe Path                 | /Users/wanwan/Desktop/hw2-zishuma-lgtm-main/_data/fed_funds_futures.parquet                                             |


**Linked Charts:**


- [hw2:fedwatch_latest_forecast](../../charts/hw2.fedwatch_latest_forecast.md)



## Pipeline Manifest

| Pipeline Name                   | HW 2: The Yield Curve and the Policy Path                       |
|---------------------------------|--------------------------------------------------------|
| Pipeline ID                     | [hw2](../../../index.md)              |
| Maintainer                      | Jeremiah Bejarano               |
| Contributors                    | Jeremiah Bejarano |
| Repository                     | https://github.com/hw-finm-32800/hw2                  |
| Pipeline Web Page               | <a href="file:///Users/wanwan/Desktop/hw2-zishuma-lgtm-main/docs/index.html">Pipeline Web Page      |
| Date of Last Code Update        | 2026-10-24 14:44:52           |
| OS Compatibility                | Windows, Linux, macOS |
| Linked Dataframes               |  [hw2:crsp_treasury_consolidated](../../dataframes/hw2/crsp_treasury_consolidated.md)<br>  [hw2:fed_yield_curve](../../dataframes/hw2/fed_yield_curve.md)<br>  [hw2:fed_funds_futures](../../dataframes/hw2/fed_funds_futures.md)<br>  |


**Build Commands:**
```
doit

```

