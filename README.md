# ds-assignment2-cleaned-data
Cleaned Netflix and Supermarket Sales datasets (v1.0) for Data Science Assignment 2, FAST-NU. Used for EDA and Assignment 3.
# Netflix & Supermarket Sales – Cleaned Datasets

Cleaned datasets for **CS4048 Data Science, Assignment 2 (EDA)**, FAST-NU Lahore.
They will be reused in Assignment 3.

**Version:** v1.0 | **Date:** 17 October 2026 | **Author:** Kashaf Zahra (23L-0766)

## Files

| File | Rows x Columns |
|---|---|
| `23L_0766_A2_netflix_cleaned.csv` | 8,807 x 28 |
| `23L_0766_A2_supermarket_cleaned.csv` | 1,000 x 24 |

## Original sources

- **Netflix:** Netflix Movies and TV Shows by Shivam Bansal, on Kaggle:
  https://www.kaggle.com/datasets/shivamb/netflix-shows
- **Supermarket Sales:** `supermarket_Sales.csv`, provided by the course instructor.

The original data belongs to its authors. Please credit them and follow the Kaggle licence.

## What I changed

**Netflix**
- Removed extra spaces and converted `date_added` to a real date.
- Three rows had durations (like "74 min") inside `rating`. I moved them to `duration`.
- Missing `director`, `cast` and `country` were filled with "Unknown", with `has_*` columns to mark them.
- Split `duration` into `duration_min` (movies) and `n_seasons` (TV shows).
- Added new columns: `year_added`, `month_added`, `release_to_added_gap`, `n_countries`,
  `n_genres`, `n_cast`, `primary_country`, `primary_genre`, `rating_group`, and a few more.
- No rows were deleted. Unusual values (very short or long movies, shows with many seasons) were kept because they are real titles.

**Supermarket Sales**
- No missing values, duplicates or errors were found, so no rows were changed or removed.
- `Date` was converted to YYYY-MM-DD format.
- Added `datetime`, `month`, `day_of_month`, `weekday`, `is_weekend`, `hour` and `time_of_day`.
- Note: `Cost of goods sold`, `Tax 5%`, `Total` and `Gross income` can all be calculated from
  `Unit price x Quantity`, and `Gross margin percentage` is always the same value.
  They were kept so the file matches the original.

## How to load

```python
import pandas as pd
base = "https://raw.githubusercontent.com/Kashaf-Zahraa/ds-assignment2-cleaned-data/v1.0/"
netflix = pd.read_csv(base + "23L_0766_A2_netflix_cleaned.csv")
supermarket = pd.read_csv(base + "23L_0766_A2_supermarket_cleaned.csv")
```

## Version history

- **v1.0** (17 Oct 2026): first release.
