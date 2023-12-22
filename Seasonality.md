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
<hr>

### Let's address both of the _suspects_

The seasonal component, particularly its phases, is crucial. Utilizing Fourier Analysis, we perform a Fourier transform to extract the mode corresponding to the annual cycle. Given the monthly data, this corresponds to a periodicity of 12 months (after frequency transformation).

Assessing all beer styles along with their phases enables us to identify which styles contribute to seasonality and during which phase (time of the year).

#### Fourier Analysis for Europe:

![Fourier analysis for EU](./plots/fft_beer_style_eu.png)

#### Fourier Analysis for North America:

![Fourier analysis for NA](./plots/fft_beer_style_na.png)

- **Observation:**
  - EU data is overall much noisier, as expected from the initial seasonality plot, resulting in reduced peaks. This normalization allows us to filter out very noisy data without a main peak in a yearly cycle.
  - Only a few styles contribute significantly to seasonality, motivating the filtering of styles without significant differences at a 12-month period.
  - Some beers, like **Dark Lagers**, show a mode at 10 months but not (or only marginally) at 12 months.

![Normalised FT of filtered beer styles](./plots/normalised_fft_eu_na.png)

- **Observation:**
  - The FT plots look cleaner with only significant contributors to annual periodicity remaining.
  - There are additional modes, not further investigated here, notably in North America with Dark Lagers at 8- and 10-month cycles.
  - NA has more beers with significant seasonality than EU.

In the next step, we summarize and display our findings, combining phase information.

#### Beer Style Contributors of Seasonal Component:

![Beer style contributors of seasonal component](./plots/contributors_beer_styles.png)

- **Observation:**
  - **Specialty Beer** contributes the most to seasonality, given its huge seasonal effect.
  - Styles like **IPA** show a remarkable contribution to seasonality in North America.
  - EU and NA share similar contributing styles, but with variations in order and magnitude.
  - Wheat beers or Hybrids contribute more in EU than in NA.

An important factor is missing: **The phase**. We don't yet see which contribution peaks in ABV at what time of the year! To present the final result of seasonality, we intend to summarize all findings in one plot.

#### Peak Seasonality Plot:

<iframe width="800" height="600" frameborder="0" seamless="seamless" scrolling="no" src="./plots/html/peak_seasonality.html"></iframe>

- **Observation:**
  - Approx. 80% of the seasonal contribution in North America peaks in the winter months (Dec.-Feb.), compared to around 65% in Europe.
  - The effect of **Oktoberfest** is visible with a peak contribution from Dark Lagers each October in Europe.
  - Europe has a second peak in May, driven by Porters and Strong Ales.
  - This second peak seems to be the main difference in seasonality patterns between Europe and North America.

To recall the initial seasonality, we highlight the off-peak contributions from Porters (EU only) and Dark Lagers.

![Seasonality highlighted in May and October](./plots/seasonality_may_oktober_highlighted.png)

- **Observation:**
  - EU shows a clear plateau each May.
  - Oktoberfest is barely noticeable here.
  - North America often holds the peak value longer, due to styles peaking their contribution in February as well.

#### So regarding all the above we can release the suspects <sub>for now</sub>.
