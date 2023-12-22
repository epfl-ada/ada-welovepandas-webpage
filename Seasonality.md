---
layout: default
---

# Seasonality

### Why is there a seasonality trend betweeen Europe and North America?

We will try to answer this question by first decomposing the time series for each region into seasonality and trend:

![Seasonality; NA vs EU](./plots/seasonality_na_vs_eu.png)

- _We observe that both regions have a clear seasonality pattern. But in Europe there is more noise present and there is second peak, which seems to be appearing in spring. What could be the reason for this?_
- _The trend seems to be linearly increasing for both continents, even though it is clearly higher for NA users._

We suspect that the difference in the seasonality pattern of American and European ratings might be due to big beer events that take place in Europe, such as Oktoberfest, which is in fact the world's largest beer festival and it takes in late September and the first weekend of October.

To be sure, we will have a closer look at the trend and the seasonality (including residuals):

![Seasonality](./plots/seasonality.png)
_When keeping the residuals, the second peak in Europe looks more like a plateau, where North America seems to drop more quickly._

What could be the reason for the second peak??

<br>

![St. Patrick](./gifs/stpatrick.gif)

<br>

Have you ever heard of St. Patrick's Day?

- It is an Irish traditional holiday, taking place in March.

This might be the reason for the second peak appearing in spring!

Maybe looking at the seasonality of beer styles will help us understand its cause better? -> [Beer style seasonality](/Beer%20style%20seasonality)

To analyse the contributions and phases of the seasonality pattern more, we will further use a Fourier Analysis -> [FT seasonality analysis](/FT%20analysis)
