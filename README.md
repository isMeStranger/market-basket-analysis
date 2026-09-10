# Market Basket Analysis

This project analyzes the Dunnhumby "The Complete Journey" market basket dataset, which
records grocery purchases at the line item level: quantity, sales value, discounts, store,
household, product and basket.

## Scope

The analysis covers shopping behavior in a few areas:

* basket metrics, like the number of items per basket and the total basket value
* descriptive statistics for quantity, sales value and discounts
* top products, top stores and top households
* sales volume by calendar week and by hour of day
* a correlation heatmap across the continuous variables

## Public kernel

* Kaggle kernel: https://www.kaggle.com/code/salarsabry/market-basket-analysis
* Dataset: https://www.kaggle.com/datasets/frtgnn/dunnhumby-the-complete-journey

## Reproduce

```bash
kaggle kernels push
kaggle kernels status salarsabry/market-basket-analysis
kaggle kernels output salarsabry/market-basket-analysis -p out/
```

Artifacts written to `out/`: `summary.json`, `descriptive_stats.csv`, `correlations.csv`,
`top_products.csv`, `top_stores.csv`, `top_households.csv`, `sales_by_day.csv`,
`sales_by_hour.csv`, plus PNG plots.

## Files

```text
market-basket-analysis.ipynb  # the analysis notebook
kernel-metadata.json          # kernel runtime configuration
```

## Dataset notes

* `DAY` is a running counter of study days (1..711), not a day of the week; `WEEK_NO`
  (1..102) is the calendar week.
