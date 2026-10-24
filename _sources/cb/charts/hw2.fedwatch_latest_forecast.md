---
date: "2026-10-24 14:44:52"
tags: "CME Globex"
category: "Monetary Policy, Futures, Fedwatch"
---

# Chart: FedWatch: Next FOMC Meeting Probabilities
Market-implied probabilities of the next FOMC rate decision from 30-Day Fed Funds futures

## Chart
```{raw} html
<iframe src="../../_static/hw2/fedwatch_latest_forecast.html" height="500px" width="100%"></iframe>

<p style="text-align: center;">Sources: CME Globex</p>
```
[Full Screen Chart](../download_chart/hw2/fedwatch_latest_forecast.html)




# FedWatch: Next FOMC Meeting Probabilities

Probability of each fed funds target-range outcome at the next scheduled FOMC
meeting, implied by 30-Day Fed Funds futures (ZQ) prices. This replicates the
simplest case of the
[CME FedWatch tool](https://www.cmegroup.com/markets/interest-rates/cme-fedwatch-tool.html).

**Method.** A ZQ contract settles at 100 minus the calendar-day average EFFR
over its month. The latest realized EFFR print (published by the New York
Fed) pins the pre-meeting rate r_pre. (The published tool reads that rate
from the futures contract for the nearest month with no FOMC meeting
instead.) The meeting-month contract prices a day-weighted average,
r_avg = (d/N)·r_pre + ((N−d)/N)·r_post, where the meeting ends on day d of an
N-day month; solving gives the expected post-meeting rate r_post. Assuming
the only outcomes are "no change" and a single 25 bp move,
P(move) = |r_post − r_pre| / 0.25.

**Caveats.** When the meeting falls in the last few days of a month, the
next month's contract is read directly instead (as FedWatch does); for a day
or two after each decision the EFFR anchor may not yet reflect the new
target; multi-meeting probability trees and moves larger than 25 bps are out
of scope. See the notebook *Replicating the CME FedWatch Tool* for the full
derivation.



## Chart Specs

| Chart Name             | FedWatch: Next FOMC Meeting Probabilities                                                   |
|------------------------|------------------------------------------------------------|
| Chart ID               | fedwatch_latest_forecast                                               |
| Tags                   | Monetary Policy, Futures, Fedwatch                                      |
| Data Series Start Date |                                              |
| Data Frequency         | Daily                                              |
| Observation Period     |                                      |
| Lag in Data Release    |                                             |
| Data Release Timing    |                                          |
| Seasonal Adjustment    |                                     |
| Units                  | Probability (%)                                                  |
| HTML Chart             | [HTML](../download_chart/hw2/fedwatch_latest_forecast.html)    |


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
| Data available up to (min)     |                                                              |
| Data available up to (max)     |                                                              |
| Dataframe Path                 | /Users/wanwan/Desktop/hw2-zishuma-lgtm-main/_data/fed_funds_futures.parquet                                             |


**Linked Charts:**


- [hw2:fedwatch_latest_forecast](../../charts/hw2.fedwatch_latest_forecast.md)



## Pipeline Manifest

| Pipeline Name                   | HW 2: The Yield Curve and the Policy Path                       |
|---------------------------------|--------------------------------------------------------|
| Pipeline ID                     | [hw2](../../index.md)              |
| Maintainer                      | Jeremiah Bejarano               |
| Contributors                    | Jeremiah Bejarano |
| Repository                     | https://github.com/hw-finm-32800/hw2                  |
| Pipeline Web Page               | <a href="file:///Users/wanwan/Desktop/hw2-zishuma-lgtm-main/docs/index.html">Pipeline Web Page      |
| Date of Last Code Update        | 2026-10-24 14:44:52           |
| OS Compatibility                | Windows, Linux, macOS |
| Linked Dataframes               |  [hw2:crsp_treasury_consolidated](../dataframes/hw2/crsp_treasury_consolidated.md)<br>  [hw2:fed_yield_curve](../dataframes/hw2/fed_yield_curve.md)<br>  [hw2:fed_funds_futures](../dataframes/hw2/fed_funds_futures.md)<br>  |


**Build Commands:**
```
doit

```
