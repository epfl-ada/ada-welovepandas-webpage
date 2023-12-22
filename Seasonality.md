---
layout: default
---

# Seasonality

---

## Why is there a seasonality trend between Europe and North America?

We will try to answer this question by first decomposing the time series for each region into seasonality and trend.

![Seasonality; NA vs EU](./plots/seasonality_na_vs_eu.png)

From the graph above, we can conclude the following points:

- Both regions show a clear seasonality pattern. However, in Europe, there is more noise present, and there is a second peak, which seems to appear in spring. What could be the reason for this?
- The trend seems to be linearly increasing for both continents with a similar slope. Although North America definitely shows higher ABV on average at all times!

---

### Question: What are the suspects which are the reason for seasonality?

### Oktoberfest <sup>Suspect 1</sup>

We suspect that the difference in the seasonality pattern of American and European ratings might be due to significant beer events that take place in Europe, such as **Oktoberfest**, which is, in fact, the world's largest beer festival and takes place in late September and the first weekend of October.

### Fresh and light during Summertime <sup>Suspect 2</sup>

Have you ever relaxed at a beach in summer, with your sun glasses on, sipping gently on your 12% Russian Imperial stout? Yes... Me neither. We suspect that people tend to drink lighter beers overall during hot summer days and rather prefer stronger kinds of beer during the colder parts of the year. This does not seem too unlikely, given that the seasonality pattern in both continents show higher ABV during winter periods on average than during summer!

To be sure, we will take a closer look at the trend and the seasonality (including residuals):

![Seasonality](./plots/seasonality.png)

_When keeping the residuals, the second peak in Europe looks more like a plateau, where North America seems to drop more quickly._

### St. Patrick's Day <sup>Suspect 3</sup>

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
<hr>

### Let's address both of the _suspects_

Since Guinness, and Stouts in general, are rather on the strong side of beer spectrum, an increase in consumption could easily spark a peak in the ABV pattern.

In a simple approach to investigate this, we decided to decompose the seasonality of each beer style into Fourier modes by running a simple discrete Fourier transform over it. Naturally converting from frequency space to periodicity space allows to easily filter beer styles that show a significant mode corresponding to a 12-month period.

Comparing the amplitudes and accounting for the popularity of the beer style, in addition to extracting the phase shift of the peaks, allows us to gain deeper insight on what the seasonality is composed of.

After some filtering for months that contribute to seasonality, a normalised Fourier transform would look like this:

<br>

![Normalised FT of filtered beer styles](./plots/normalised_fft_eu_na.png)

- **Observation:**
  - We observe modes for each of those beer styles corresponding to a periodicity of 12 months $\rightarrow$ seasonality!
  - There are additional modes from certain styles such as at 10 months, which we do not investigate further here, because 10-month periodicity does not correspond to how we define seasonality
  - There is much more noise in the European data than in the North American data overall
  - More beer styles are involved with seasonality in North America in comparison to Europe, also not necessarily the same beer styles contribute to seasonality!

We can summarise all the information, including the phase shift, which equals the peak ABV of the oscillation here in a fancy graph:

#### Peak Seasonality Plot

<iframe width="800" height="600" frameborder="0" seamless="seamless" scrolling="no" src="./plots/html/peak_seasonality.html"></iframe>

- **Observation:**
  - Approx. 80% of the seasonal contribution in North America peaks in the winter months (Dec.-Feb.), compared to around 65% in Europe.

  - We even can confirm our first suspect! **Oktoberfest** shows its face (or peak) on both continents each October in the form of a contribution from Dark Lagers, which contains among others **Märzen** as well as **Oktoberfestbeer**! Although the overall contribution to the total is only $\sim 5$%

  - We also observe styles such as **Indian Pale Ale**, which showed marginal seasonality overall to have a larger contribution in America and pretty much none in Europe. We can recall here that due to the huge popularity in North America, even a slight seasonal change in ABV can have a strong overall effect if enough people drink (and rate) it.

  - To our disappointment, St. Patricksday could not be confirmed. We observe the second peak in May, which is too late, and in the form of **Strong Ales** and **Porters** which peak only in Europe each year, a group of rather strong beers seems to gain popularity each May of every year.

Let us recall our initial trends, highlighting the months of May and October:

![Seasonality highlighted in May and October](./plots/seasonality_may_oktober_highlighted.png)

<br>

- The second peak in Europe occurs in May, which is due to **Strong Ales** and **Porters**.
- Europe declines quicker after its winterly peak than North America does. We do see multiple styles such as **IPA** having their peak only in February which explains the longer upkeep of high ABV 
