# Zillow-Rent-Analysis
Cleaning a messy, real-world Zillow scrape and answering five business questions about rent in Southern Californian cities.

## Problem

Rent depends on many things at once: home size, location, and how fast a listing moves. Looking at raw rent numbers hides this. A city can look expensive just because its homes are big. This project cleans a raw web-scraped dataset and answers: **what actually drives rent, and where is the market expensive or competitive?**

## Data

- Zillow rental listings for Orange County, CA (2025), **web scraped using [Apify](https://apify.com)**.
- Raw size: 2,500 rows and 300 columns. After cleaning: 1,892 rental listings plus 604 apartment buildings analyzed separately.
- Dataset on Kaggle: [zillow-rental-market-data-california-2025](https://www.kaggle.com/datasets/sv1802/zillow-rental-market-data-california-2025)

## Cleaning (the hard part)

- Cut **300 columns down to 23**, one documented reason at a time (163 were photo links).
- Found that the "missing" rents were not errors: 604 rows are apartment buildings that list starting prices per unit type, so I split them into two tables and reshaped the building prices.
- Removed mobile home rows with sale prices listed as rent, blanked an impossible 10 sq ft area, merged "Dana Pt" and "Dana Point", converted dates and `$2,499+` text into numbers.
- Kept luxury rentals (real data) and used **medians** instead of means.

## Questions and answers
