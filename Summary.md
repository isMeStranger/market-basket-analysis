# Market Basket Analysis, a Summary

This document collects the main findings from the analysis of the Dunnhumby Complete Journey dataset. It is meant for anyone who wants the key numbers at a glance, without reading the whole notebook.

## The dataset

* 2,595,732 purchased line items in total
* 276,484 shopping trips, or baskets
* 2,500 households
* 92,339 distinct products
* 582 stores
* purchases span 102 calendar weeks, and DAY runs from 1 to 711 as a running counter of study days, not a day of the week
* no missing values, and no returns (no negative sales values)

## Prices, quantities and discounts

* the average price on a line is $3.10, the median is $2.00, and the largest single line is $840.00
* the average quantity on a line is 100.4, while the median is 1; the average is pulled up by a few large purchases, so most lines hold a single item
* 1,303,026 lines, or 50.2% of the file, carry a retail discount, which is stored as a negative value
* 36,422 lines, or 1.40%, carry a coupon discount

## The typical basket

* 9.39 distinct items on average, with a median of 5
* the average basket value is $29.14, and the median is $17.07
* 2.47 departments on average
* 83.4% of baskets contain at least one discounted item, and 6.1% contain a coupon item
* baskets with a coupon item are worth $67.56 on average, while baskets without one are worth $26.66

## Where the money comes from

* 11,865 products cover 80% of all sales
* the 100 most popular products already account for 18.3% of sales
* the top 10% of households account for 34.3% of sales, and the top 100 households for about 17.8%

## What people buy together, product level

A rule here is a pair of products that appears in the same basket. Support is the share of baskets that held both. Confidence is the chance that the second product is in the basket when the first one is there. Lift compares what we see with what we would expect if the two products were independent, so a lift above 1 means they go together more often than chance.

* among the 100 most frequent products, 1181 pairs reach a lift above 1.5 at a support of at least 0.0005
* the strongest links are pairs of similar items, for instance two shelf stable vegetable packs (lift 41.8), two soft drink singles (lift 34.1), or bread and hot dogs (lift 13.7)
* the most common pairs by volume are milk with tropical fruit (3,447 baskets), eggs with tropical fruit (2,539 baskets), and berries with tropical fruit (2,350 baskets)
* the full list of pairs is in `product_pairs.csv`, and the stronger ones in `product_pairs_strong.csv`

## What people buy together, department level

* by sales, the leading departments are `GROCERY`, `DRUG GM`, `PRODUCE`, `MEAT`, `KIOSK-GAS`
* once we only look at pairs that appear often enough, the strongest links are `MEAT` with `SEAFOOD-PCKGD` (lift 2.63) and `MEAT-PCKGD` with `SEAFOOD-PCKGD` (lift 2.61)
* the most common combinations pair `DRUG GM` with `GROCERY`, found in 95,238 baskets, and `GROCERY` with `PRODUCE`, found in 84,148 baskets
* department pairs are ranked by lift only once their support clears 0.005, because pairs that almost never happen produce unreliable lift; everything lives in `department_pairs.csv` and `department_performance.csv`

## When people shop

* the busiest hour is 17:00, with 269,682 lines
* the busiest week is WEEK_NO 92, with 33,126 lines
* stores are open from 07:00 to 23:30 and the busiest hours sit in the late afternoon and evening; weekend patterns cannot be derived directly because DAY counts study days rather than weekdays

## Households

* household demographics are available for 801 of the 2,500 households, and this copy of the dataset does not include income fields
* among households with demographics, the sales split by composition is 2 Adults No Kids 32.3%; 2 Adults Kids 26.9%; Single Female 15.7%; Single Male 10.2%; Unknown 8.5%; 1 Adult Kids 6.4%
* see `household_composition_segments.csv` and `top_households.csv`

## Correlations between the main numbers

* quantity and sales value correlate at 0.59
* sales value and retail discount correlate at 0.25 with a negative sign, which simply reflects that discounts lower the posted value
* WEEK_NO and DAY correlate at 1.00, since both count the passage of time

## Reading the results with care

* what happens together is not the same as what causes what; these patterns describe baskets, they do not prove cause
* the product level rules cover the 100 most frequent products, a small and popular slice of the catalog
* averages hide the spread between baskets, so basket level numbers pair well with the descriptive stats in `descriptive_stats.csv`
* week numbers start at 1 and only matter relative to this study, so treat them as study relative rather than calendar weeks

## What this means for the business

* sales concentrate heavily in a small set of products, so assortment and stocking should center on the top products and the pairs that sell together
* the strongest links are chances to bundle, place products side by side, or run promotions that lift the basket
* coupon shoppers spend more per basket, which suits basket building promotions
* the peak hours, roughly 14:00 to 20:00, and the busy weeks are the natural slots for staffing and promotions
