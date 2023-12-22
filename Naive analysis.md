---
layout: default
---

# Naive analysis

---

Moving straightforward to our research question:

**Do Americans prefer beers with higher alcohol content (ABV) than Europeans?**

---> We investigate the average rating that EU and NA users give, for each ABV rounded percentage.

![Average ABV](./plots/Avg_ABV.png)

- _It seems like NA users tend to give better ratings in general, but we don't see a large difference_
- _Ratings are higher for beers with higher ABV to a certain point (15%), but then drop for both continents_

We also want to investigate if the number of ratings per rounded ABV percentage has to do something with the average rating per ABV?

![Count beers with certain ABV](./plots/count_abv.png)

_Beers with ABV lower than 5% or greater than 15% have fewer number of ratings. If only few users rated, and graded them good, this results in better average rating for the specific ABV._

Another question arises out of curiosity:
**Is there a correlation between preference and a specific beer style known for higher ABV?**

Let's investigate this question:

[Beer styles](/ada-welovepandas-webpage/Beer%20styles)
