# Week 08 - Work with table: 1D analysis and 2D analysis

<div id="toc">
<!-- TOC -->

- [Week 08 - Work with table: 1D analysis and 2D analysis](#week-08---work-with-table-1d-analysis-and-2d-analysis)
    - [Objective](#objective)
    - [Distribution](#distribution)
        - [Histogram and KDE](#histogram-and-kde)
            - [Bonus: How histograms can be cheating](#bonus-how-histograms-can-be-cheating)
        - [Special points in distribution](#special-points-in-distribution)
    - [Articulate central tendency and spread of data](#articulate-central-tendency-and-spread-of-data)
        - [Variance, skewness, kurtosis](#variance-skewness-kurtosis)
    - [Correlation](#correlation)
        - [Continuous: Scatter plot and correlation](#continuous-scatter-plot-and-correlation)
        - [Discrete: Cross-tab and correlation](#discrete-cross-tab-and-correlation)
        - [From correlation to causality](#from-correlation-to-causality)
    - [Bonus: (Statistical) Hypothesis testing](#bonus-statistical-hypothesis-testing)

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

The dataset and case we use this week comes from a workshop called "descriptive analysis" conducted by Jenifer on GICJ2017 in South Africa. You can download data from:

* www.jenster.com/nottingham.xlsx
* www.jenster.com/index.xlsx

New modules:

* [Matplotlib](https://matplotlib.org/). Matplotlib is a Python 2D plotting library and one of the most frequently used plotting modules in Python.
* [Seaborn](https://seaborn.pydata.org/). Seaborn is a Python data visualization library based on matplotlib. It provides a high-level interface for drawing attractive and informative statistical graphics.

## Distribution

### Histogram and KDE

```python
import pandas as pd
from matplotlib import pyplot as plt
import seaborn as sns
import numpy as np
df = pd.read_excel('nottingham.xlsx')
df.describe() #get descriptive information
```

![Df describe](assets/df_describe.png)

The columns:

* `AVG_ENG_MATH_SCORE_xx`: The average score for the particular class of year xx. For a class, this metric is the higher the better
* `P_ABSENT_PERSIST`:  the absent ratio transformed somehow, the higher the worse.

This is multi dimensional data. We are interested in the relationship between those dimensions/ variables.

```python
len(df)
df['P_ABSENT_PERSIST'].hist(bins=20)
```

![Dataframe hist](assets/df_hist.png)

Quick Question:
* What do you conclude from this histogram?
* What would you do next to mine the news?

```python
df['AVG_ENG_MATH_SCORE_07'].hist(bins=20)
```

![Dataframe hist](assets/df_hist2.jpg)

Same question: can you find anything notable from this chart? It that weird for the outlier whose score is around 15? How do we filter that out?

```python
df[df['AVG_ENG_MATH_SCORE_07'] < 16]
```

![Filter Outlier](assets/filter_outlier.png)

#### Bonus: How histograms can be cheating

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

## Bonus: (Statistical) Hypothesis testing

