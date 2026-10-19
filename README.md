# Household Electricity Forecasting — SDG 7

## Project overview
This capstone project aims to help households anticipate their next-day
electricity consumption and support informed energy-use planning.

The project aligns with SDG 7, particularly Target 7.3 on energy efficiency.
Assignment 1 includes data preparation, an initial Random Forest forecasting
experiment, baseline comparisons and a project proposal.
A user-facing application is planned for the next stage.

## Team — Group 7
- Burak Arslan
- Buğra Karatepe
- Zeynep Erva Akdoğan
- Zeynep Şura Çetin

## Dataset
We use the UCI Individual Household Electric Power Consumption dataset.

- One household in Sceaux, France
- December 2006 to November 2010
- 2,075,259 minute-level records
- License: CC BY 4.0

Source: https://archive.ics.uci.edu/dataset/235/individual+household+electric+power+consumption

Citation: Hebrail, G. & Berard, A. (2006).
Individual Household Electric Power Consumption.
UCI Machine Learning Repository. https://doi.org/10.24432/C58K54

## Data preparation
Date and time were combined, and measurements were converted to numeric values.
Missing values, duplicate timestamps and negative measurements were checked.

Hourly energy in kWh was calculated by summing 60 minute-average active power
measurements in kW and dividing by 60.

- Complete hourly intervals: 34,085
- Incomplete hourly intervals: 504
- Missing consumption values were not imputed or replaced with zero.
- The hourly time grid was preserved before creating lag features.

After requiring complete model inputs and 24 usable hours per day,
1,080 eligible days remained.

## Model and evaluation
Random Forest predicts each hour of the next day using:
- Hour, weekday, month and weekend indicator
- Consumption at the same hour 1, 2, 3 and 7 days earlier
- Previous complete day's mean and maximum hourly consumption

Configuration:
200 trees, maximum depth 15, minimum leaf size 5, random seed 42.

The eligible days were split chronologically:
- Training: 864 days / 20,736 hours
- Testing: 216 days / 5,184 hours

Training dates: 25 December 2006–20 February 2010.
Test dates: 22 February 2010–25 November 2010.

These are selected complete days, not continuous calendar periods.
The model was trained once. Each test day was forecast using only information
available at the beginning of that day. Observed consumption from earlier
test days was therefore available for later daily forecasts.

## Initial results

| Method | MAE (kWh) | RMSE (kWh) |
|---|---:|---:|
| Previous day, same hour | 0.5134 | 0.7662 |
| Previous week, same hour | 0.5546 | 0.8047 |
| Random Forest | 0.4205 | 0.5827 |

Random Forest reduced MAE by approximately 18.1% compared with the
previous-day baseline. This is a reduction in forecasting error,
not a measured reduction in electricity consumption.

![First test day forecast](SDG7%20Assignment1/first_test_day_forecast.png)

The chart shows the first test day. The results table covers all test hours.

## Repository files

| File | Purpose |
|---|---|
| SDG7_Assignment1_Proposal.pdf | Two-page project proposal |
| Untitled0.ipynb | Data preparation, model training and evaluation |
| household_hourly_clean.csv | Hourly consumption and data-quality indicators |
| model_comparison.csv | Evaluation metrics for the three methods |
| test_predictions.csv | Actual consumption and predictions for test hours |
| first_test_day_forecast.png | Example forecast chart |

## How to run in Google Colab
1. Open the SDG7 Assignment1 folder and download Untitled0.ipynb.
2. Open https://colab.research.google.com/ and upload the notebook.
3. Download the original dataset from the UCI link above.
4. Extract household_power_consumption.txt from the downloaded ZIP.
5. Upload the TXT file using Colab's Files panel.
   Its path must be /content/household_power_consumption.txt.
6. Run the notebook cells in order from top to bottom.

The notebook uses pandas, NumPy, scikit-learn and Matplotlib.
If these packages are missing, run this in a new first code cell:

    %pip install pandas numpy scikit-learn matplotlib

The notebook generates the hourly CSV, evaluation results, predictions
and a chart. It also triggers downloads through Google Colab.

The original TXT file is required to run the notebook from the beginning.
The hourly CSV is a derived output and does not replace that input.

## Limitations and responsible use
- Results are based on one historical household and may not generalize.
- Complete-day filtering excludes periods with missing inputs or targets.
- Weather, occupancy and appliance schedules are not included.
- High consumption does not automatically indicate waste.
- Forecasts are estimates; energy or bill savings have not been demonstrated.
- Future household uploads should be handled privately because consumption
  patterns may reveal personal routines.

## SDG reference
United Nations — Goal 7, Target 7.3:
https://sdgs.un.org/goals/goal7
