# Dataframe: `hw2:fed_yield_curve` - Federal Reserve Yield Curve

Daily zero-coupon yields (SVENY01 to SVENY30, in percent) implied by the Nelson-Siegel-Svensson curve that Gurkaynak, Sack, and Wright estimate and the Federal Reserve Board publishes.


## DataFrame Glimpse

```
Rows: 17048
Columns: 31
$ SVENY01          <f64> 4.4896
$ SVENY02          <f64> 4.6918
$ SVENY03          <f64> 4.7785
$ SVENY04          <f64> 4.8199
$ SVENY05          <f64> 4.8497
$ SVENY06          <f64> 4.8828
$ SVENY07          <f64> 4.9241
$ SVENY08          <f64> 4.9736
$ SVENY09          <f64> 5.0293
$ SVENY10          <f64> 5.0888
$ SVENY11          <f64> 5.1496
$ SVENY12          <f64> 5.2096
$ SVENY13          <f64> 5.267
$ SVENY14          <f64> 5.3205
$ SVENY15          <f64> 5.3692
$ SVENY16          <f64> 5.4126
$ SVENY17          <f64> 5.4502
$ SVENY18          <f64> 5.4819
$ SVENY19          <f64> 5.5077
$ SVENY20          <f64> 5.5276
$ SVENY21          <f64> 5.5418
$ SVENY22          <f64> 5.5505
$ SVENY23          <f64> 5.554
$ SVENY24          <f64> 5.5526
$ SVENY25          <f64> 5.5465
$ SVENY26          <f64> 5.5361
$ SVENY27          <f64> 5.5216
$ SVENY28          <f64> 5.5033
$ SVENY29          <f64> 5.4816
$ SVENY30          <f64> 5.4566
$ Date    <datetime[ns]> 2026-10-16 00:00:00


```

## Dataframe Manifest

| Dataframe Name                 | Federal Reserve Yield Curve                                                          |
|--------------------------------|--------------------------------------------------------------------------------------|
| Dataframe ID                   | [fed_yield_curve](../dataframes/hw2/fed_yield_curve.md)                                       |
| Sources                        | Federal Reserve                                          |
| Providers                      | Federal Reserve Board                                        |
| Provider Links                 | https://www.federalreserve.gov/data/nominal-yield-curve.htm                                   |
| Tags                           | Treasury, Yield Curve, Federal Reserve                                             |
| Access Types                   |                                       |
| How is data pulled?            | Web download via Python                                                   |
| Data available up to (min)     | 2026-10-16 00:00:00                                                             |
| Data available up to (max)     | 2026-10-16 00:00:00                                                             |
| Dataframe Path                 | /Users/wanwan/Desktop/hw2-zishuma-lgtm-main/_data/fed_yield_curve.parquet                                             |


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

