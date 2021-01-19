# UMH-Plots

This repository includes code, data and output for understanding the relationship between urbanization and common mental disorders (i.e., Anixety, Depressive and Substance use). These plots are generated for a paper written by the Centre for Urban Mental Health (http://bit.ly/umh-uva).

The plots are generated using Python and the plotly package.

## Datasets used
The plots use freely available data from:
1. GBD - [http://ghdx.healthdata.org/](http://ghdx.healthdata.org/)
2. Gapminder [https://www.gapminder.org/data/](https://www.gapminder.org/data/)

The GBD data can be downloaded with the permalink: [here](http://ghdx.healthdata.org/gbd-results-tool?params=gbd-api-2019-permalink/c28e0baacd911b17c2f5ea1af0aca42e) this includes the parameters used to download the CSV file

The Gapminder data includes two data sets:
1. Urban Population as % Total
2. Population Total

All datasets are available in the repository, inside the data folder. The datasets are merged into one dataframe, which is also exported to csv and available int he data folder of this repository.


## Plot details

These plots show various analyses of how common mental disorders are related to urbanisation.
In general we see a positive correlation for all CMDs and urbanisation.

We provide a number of different plots:

* We construct a non-parametric (lowess) trendline that seems to suggest some non-linearity and that countries with more than 50%-60% urbanisation suffer more.
* Lowess fits are non-parametric fits that are ideally suited for exploring patterns in real data<sup>[[1]](#lowess)</sup>
. They perform locally weighted regression around the data points to highlight patterns, and as such do not ascribe some theoretical fit to the data (in this case Rˆ2 and other statistical measure aren't applicable). To give some indication of the stability of the lowess fit, we perform a bootstrap of the lowess fit using a sample size of 0.5 x N<sup>[[2]](#Nsize)</sup>: and  500 samples. Using these bootstrapped lowess fits we plot the 95% confidence intervals from all 500 fits (indicated by the shaded region).
* We show a bubble plot with markers (representing countries) scaled by the total population. This plot clearly shows there is no significant correlation with CMD rate and country size.
* For completeness we show the same plot with an ordinary least square fit (quality of fits is also available in the code). This again shows a positive correlation for all CMDs, but the quality of the fits is poor and the lowess plot already suggests a more complex non-linear relationship.
* The data from GBD regarding the rate of CMDs includes an upper and lower bound for each estimate. We include a plot to show how that relative error ((upper-bound - lower-bound)/estimate) scales with the rate of urbanisation. The plot shows that countries with higher rates of urbanisation have slightly better estimates for the rate of CMDs, this is to be expected, one would expect urban living to correlate with better reporting of CMDs. However, the change in relative error does not seem to be significant enough to invalidate the general observations we have made.


<a name="lowess">[1]</a>: Cleveland, W. S. (1981) LOWESS: A program for smoothing scatterplots by robust locally weighted regression. The American Statistician, 35, 54.

<a name="Nsize">[2]</a>: N = original data set size.
