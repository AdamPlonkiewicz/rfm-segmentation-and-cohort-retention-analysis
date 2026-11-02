🇬🇧 English | [🇵🇱 Polski](README.pl.md)

# Customer Segmentation & Retention Analysis — Online Retail II

An analysis of online store customer behavior based on transactional data from 2009–2011, combining RFM segmentation with cohort-based retention analysis.

## Project Goal

The project aims to answer two related business questions:
- **Who are the store's most valuable customers, and how much do they contribute to revenue?** (RFM segmentation)
- **How does customers' likelihood of returning change depending on when they were acquired?** (cohort analysis)

The project covers the full workflow: data cleaning, exploratory data analysis (EDA), building the RFM table, customer segmentation, cohort retention analysis, and time-to-second-purchase analysis — along with documented methodological decisions and the limitations of the methods used.

## Data

The project uses the [Online Retail II](https://archive.ics.uci.edu/dataset/502/online+retail+ii) dataset from the UCI Machine Learning Repository — transactional data from a UK-based online giftware retailer covering December 2009 – December 2011.

The data file (`online_retail_II.xlsx`) is not included in the repository due to its size — download it from the UCI website and place it in the project's root directory before running the notebook.

## Methodology

**1. Data cleaning** — merging the two worksheets, removing duplicates, analyzing and removing cancelled transactions, accounting adjustments, technical codes (fees, samples, gift vouchers) and records without a Customer ID. Each removal decision was preceded by examining the characteristics of the data subset in question.

**2. RFM analysis** — calculating Recency, Frequency and Monetary values for each customer (including a description of their distributions), quintile-based scoring (`pd.qcut`), followed by segmentation into 7 customer groups based on iterative analysis supported by cross-tabulations.

**3. Cohort analysis** — assigning customers to cohorts by month of first purchase, building a retention table, analyzing M1 retention with a statistical significance test of the difference between years (`statsmodels.stats.proportion`), and analyzing time to second purchase.

## Key Findings

- The **Champions** and **Loyal Customers** segments together make up 31.4% of the customer base but account for **77.9% of sales value** — a strong concentration of value in a small part of the base.
- The **At Risk** segment (4.6% of customers) shows historical value close to that of Loyal Customers, but the median time since last purchase is 323 days — a group with high potential for selective reactivation.
- The number of newly acquired customers fell by approx. 54% in 2011 compared with 2010, even though M1 retention in comparable cohorts increased (statistically significant difference, p = 0.022) — the drop in acquisition cannot be explained by a decline in the quality of acquired customers.
- Retention after the first purchase varies seasonally — cohorts acquired in the second half of the year (the pre-holiday period) show higher retention.

Detailed findings are presented in dedicated sections of the notebook.

## Selected Visualizations

![alt text](image-1.png)


![alt text](image-4.png)


![alt text](image-3.png)

## Limitations

- RFM segmentation does not account for customer tenure (time since acquisition) — the *Recent / Low-Frequency* segment may partly include long-standing, dormant customers rather than only new ones. Details and supporting evidence (cohort × segment cross-tabulation) are in the notebook.
- The December 2009 cohort (first month of data) and the December 2011 cohort (incomplete month) are not fully comparable with the other cohorts.
- Newer cohorts have a shorter observation window, which limits comparisons over longer time horizons.

A full description of the limitations, with justification, is available in dedicated sections of the notebook.

## Repository Structure

```
├── Projekt_Retencja.ipynb    # main notebook with the full analysis
├── README.md
```
## Author

**Adam Płonkiewicz** – [LinkedIn](https://www.linkedin.com/in/adam-p%C5%82onkiewicz-762ab124a/)

## Technologies

Python, pandas, numpy, matplotlib, seaborn, statsmodels, scipy, re
