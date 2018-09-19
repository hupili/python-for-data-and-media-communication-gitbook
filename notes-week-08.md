# Week 08 - Work with table: 1D analysis and 2D analysis

<div id="toc">
<!-- TOC -->

- [Week 08 - Work with table: 1D analysis and 2D analysis](#week-08---work-with-table-1d-analysis-and-2d-analysis)
    - [Objective](#objective)
    - [Distribution](#distribution)
        - [Histogram and KDE](#histogram-and-kde)
            - [Bonus:   How histograms can be cheating](#bonus---how-histograms-can-be-cheating)
        - [Special points in distribution](#special-points-in-distribution)
    - [Articulate central tendency and spread of data](#articulate-central-tendency-and-spread-of-data)
        - [Variance, skewness, kurtosis](#variance-skewness-kurtosis)
    - [Correlation](#correlation)
        - [Continuous: Scatter plot and correlation](#continuous-scatter-plot-and-correlation)
        - [Discrete: Cross-tab and correlation](#discrete-cross-tab-and-correlation)
        - [From correlation to causality](#from-correlation-to-causality)
    - [Bonus:   (Statistical) Hypothesis testing](#bonus---statistical-hypothesis-testing)

<!-- /TOC -->
</div>

## Objective

- Master the schema of "data-driven story telling": the crowd \(pattern\) and the outlier \(anomaly\)
- Can use `pandas`, `matplotlib` and `seaborn` to conduct 1D analysis and articulate on the statistics
- Can conduct 2D analysis by:
  - `pandas.pivot_table()` -- discrete distribution analysis (bin analysis)
  - `pandas.groupby().aggreate()` -- the SAC (splitting -- applying -- combining) pattern
  - `Series.corr()` -- calculate correlation
  - `DataFrame.plot()` or `matplotlib.pyplot.plot()` -- scatter plot to visualise 2D correlation

## Distribution

### Histogram and KDE

#### Bonus:   How histograms can be cheating

Try to adjust number of bins and bin boundaries to see what happens.

### Special points in distribution

- Mean
- Max/ Min
- Median
- Percentile

* `seaborn`
* `matplotlib` 

## Articulate central tendency and spread of data

### Variance, skewness, kurtosis

## Correlation

[past reference code](https://github.com/hupili/python-for-data-and-media-communication/blob/82c813851cfb5e74d1785df86e3a9e633e810508/correlation/Cheating%20our%20children.ipynb)

### Continuous: Scatter plot and correlation

### Discrete: Cross-tab and correlation

### From correlation to causality

## Bonus:   (Statistical) Hypothesis testing

