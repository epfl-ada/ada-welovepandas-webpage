---
layout: default
---

# Seasonality

---

## Why is there a seasonality trend between Europe and North America?

We will try to answer this question by first decomposing the time series for each region into seasonality and trend.

![Seasonality; NA vs EU](./plots/seasonality_na_vs_eu.png)

From the graph above, we can conclude the following points:

- **Observation:** Both regions show a clear seasonality pattern. However, in Europe, there is more noise present, and there is a second peak, which seems to appear in spring. What could be the reason for this?
- **Trend:** The trend seems to be linearly increasing for both continents, even though it is clearly higher for NA users.

---

### Question: What are the suspects which are the reason for seasonality?

### Oktoberfest <sup>Suspect 1</sup>

We suspect that the difference in the seasonality pattern of American and European ratings might be due to significant beer events that take place in Europe, such as **Oktoberfest**, which is, in fact, the world's largest beer festival and takes place in late September and the first weekend of October.

To be sure, we will take a closer look at the trend and the seasonality (including residuals):

![Seasonality](./plots/seasonality.png)

_When keeping the residuals, the second peak in Europe looks more like a plateau, where North America seems to drop more quickly._

### St. Patrick's Day <sup>Suspect 2</sup>

<div style="display: flex; align-items: center; margin-top: 15px;">
    <div style="flex: 1;">
        <b>Have you ever heard of St. Patrick's Day?</b>
        <br><br>
        - It is an Irish traditional holiday, taking place in March.
        This might be the reason for the second peak appearing in spring!
    </div>
    <div style="flex-shrink: 0; margin-left: 20px;">
        <img src="./gifs/stpatrick.gif" width="130" height="130" alt="St. Patrick">
    </div>
</div>

<br>

<iframe src="file:///C:/Users/Lione/Repositories/ada-2023-project-welovepandas/peak_saisonality.html" width="800" height="600"></iframe>

**Note:** Maybe looking at the seasonality of beer styles will help us understand its cause better? -> [Beer style seasonality](/ada-welovepandas-webpage/Beer%20style%20seasonality)
