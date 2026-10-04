# Zillow-Rent-Analysis
Cleaning a messy, real-world Zillow scrape and answering five business questions about rent in Southern Californian cities.

Analysis can be also viewed on Kaggle: [https://www.kaggle.com/sv1802](https://www.kaggle.com/code/sv1802/zillow-rent-analysis)

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
**Q1. Which features drive rent?** Every bedroom, bathroom and square foot adds rent, but bigger homes cost less per sq ft. At the same size, a house still rents for about 40% more than an apartment.

![Median Rent by Bedrooms and Bathrooms](Plot%20images/q1_features.png)

**Q2. Which cities are actually expensive once size is accounted for?** Only Corona Del Mar, Newport Beach and Laguna Beach are expensive on both measures. Irvine has the 3rd highest rent but ranks 14th of 24 per sq ft: big homes, not pricey ones.

![Cities Analysis](Plot%20images/q2_cities.png)

**Q3. How much more does a coastal address cost?** For the same bedrooms, coastal rent is 31% to 66% higher, which is $640 to $2,700 a month.

![Coastal vs Non-Coastal Rent](Plot%20images/q3_coastal.png)

**Q4. How competitive is the market?** The typical listing is up 20 days. Price cuts jump from 20% to 41% of listings after day 30, usually by about $150.

![Price Cuts Analysis](Plot%20images/q4_price_cuts.png)

**Q5. Are apartment buildings priced differently from individual rentals?** Buildings advertise 13% to 14% more for studios and 1 beds. The gap closes by 3 beds.

![Building Types Analysis](Plot%20images/q5_buildings.png)

## Tools

Python, pandas, NumPy, matplotlib, seaborn, Jupyter. Apify for data collection.

## Limits

One 2025 snapshot of asking rents, not signed leases. Cities with fewer than 25 listings were left out of the city comparison. Building prices are "starting from" prices. The data has no amenities such as parking or laundry.

## Files

- **`zillow-rent-analysis.ipynb`**: The main Jupyter Notebook containing the full data cleaning, exploratory analysis, and visualization pipeline.
- **`Zillow Rent Data.xlsx - Data.csv`**: Uncleaned, raw, and as-is web-scraped dataset (2500 rows, 300 cols).
- **`listings_clean.csv`**: Cleaned dataset containing 1,892 individual rental listings with engineered features for downstream analysis.
- **`building_units_clean.csv`**: Reshaped dataset containing unit-level starting price tiers for 604 apartment buildings.
- **`Plot images/`**: Directory containing all 5 generated visualization charts (`.png` files) referenced in this README.
