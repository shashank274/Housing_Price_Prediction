# Housing Price Prediction

Predicts the median house value of a California district from its location, age, size and distance to the ocean. A tuned **Random Forest explains about 83% of the variation in prices**, compared with 68% for a simple linear regression.

Built with Python, pandas, seaborn and scikit-learn in a Jupyter notebook.

## The data

The California housing dataset (`housing.csv`), with **20,640 districts** from the 1990 census. Each row has:

- `longitude`, `latitude`
- `housing_median_age`
- `total_rooms`, `total_bedrooms`, `population`, `households`
- `median_income`
- `ocean_proximity` (for example `<1H OCEAN`, `INLAND`, `NEAR BAY`)
- `median_house_value`: the value to predict

Rows with missing values are dropped first.

## What the notebook does

1. **Splits** the data 80/20 into training and test sets before looking at it, so the test set stays unseen.
2. **Explores** the training data with histograms, a correlation heatmap and a map-style scatter plot of house values by latitude and longitude, which shows prices rising near the coast.
3. **Fixes skewed columns.** `total_rooms`, `total_bedrooms`, `population` and `households` are log-transformed so they look closer to a normal distribution.
4. **Encodes** `ocean_proximity` as one-hot columns.
5. **Adds two features:**
   - `bedroom_ratio` = bedrooms ÷ rooms
   - `household_rooms` = rooms ÷ households
6. **Trains and compares two models** on the same features:
   - Linear Regression
   - Random Forest, then tuned with `GridSearchCV` (5-fold cross-validation over number of trees, minimum split size and maximum depth)

The test set goes through exactly the same steps (log transform, encoding and new features) before scoring.

## Results (on the test set)

| Model | R² | Mean absolute error |
| --- | --- | --- |
| Linear Regression | 0.68 | about $47,100 |
| Random Forest | **0.83** | **about $31,600** |

Tuning with grid search picked 300 trees and a minimum split size of 4, and scored about the same as the default Random Forest (R² 0.83).

## Files

- `model.ipynb`: the full analysis
- `report.html`: an automated exploratory report (Sweetviz) of the California housing data, with a summary of every column

## Run it

```bash
git clone https://github.com/shashank274/Housing_Price_Prediction.git
cd Housing_Price_Prediction
pip install -r requirements.txt
```

Download `housing.csv` (the Kaggle "California Housing Prices" dataset), put it in this folder, then open `model.ipynb` in Jupyter.

---

More of my work: [portfolio-pied-gamma-88.vercel.app](https://portfolio-pied-gamma-88.vercel.app)
