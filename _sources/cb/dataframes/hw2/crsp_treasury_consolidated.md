# Dataframe: `hw2:crsp_treasury_consolidated` - CRSP Treasury Consolidated

Consolidated CRSP US Treasury database combining daily pricing data (prices, yields, durations) with issue-level characteristics (coupon, maturity, issue date). Sourced from WRDS.


## DataFrame Glimpse

```
Rows: 2530592
Columns: 20
$ kytreasno                  <f64> 200790.0
$ kycrspid                   <str> '19720215.104000'
$ tcusip                     <str> '912810AL'
$ caldt             <datetime[ns]> 1970-01-02 00:00:00
$ tdatdt            <datetime[ns]> 1962-11-15 00:00:00
$ tmatdt            <datetime[ns]> 1972-02-15 00:00:00
$ tfcaldt                    <i64> 0
$ tdbid                      <f64> 91.6875
$ tdask                      <f64> 91.9375
$ tdaccint                   <f64> 1.5217391304348
$ tdyld                      <f64> 0.0002223838450502
$ price                      <f64> 93.3342391304348
$ tcouprt                    <f64> 4.0
$ itype                      <f64> 1.0
$ original_maturity          <f64> 9.0
$ years_to_maturity          <f64> 2.0
$ tdduratn                   <f64> 736.7202395301399
$ tdretnua                   <f64> 0.0022468631456084
$ days_to_maturity           <i64> 774
$ callable                  <bool> False


```

## Dataframe Manifest

| Dataframe Name                 | CRSP Treasury Consolidated                                                          |
|--------------------------------|--------------------------------------------------------------------------------------|
| Dataframe ID                   | [crsp_treasury_consolidated](../dataframes/hw2/crsp_treasury_consolidated.md)                                       |
| Sources                        | CRSP                                          |
| Providers                      | WRDS                                        |
| Provider Links                 | https://wrds-www.wharton.upenn.edu/                                   |
| Tags                           | Treasury, Fixed Income, Yield Curve                                             |
| Access Types                   |                                       |
| How is data pulled?            | WRDS via Python                                                   |
| Data available up to (min)     | N/A (large file)                                                             |
| Data available up to (max)     | N/A (large file)                                                             |
| Dataframe Path                 | /Users/wanwan/Desktop/hw2-zishuma-lgtm-main/_data/TFZ_consolidated.parquet                                             |


**Linked Charts:**

- None


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

