# Housing Price Prediction

This project predicts house prices using features like location, housing attributes, and proximity to the ocean. It includes data exploration, preprocessing, feature engineering, and model training.

---

## Project Overview
- Predicts median house value based on:
  - Location data (latitude, longitude)
  - Housing attributes (total rooms, bedrooms, population, households)
  - Proximity to the ocean

---

## Technologies Used
- **Programming Language:** Python
- **Libraries:**
  - `pandas`, `numpy` for data manipulation
  - `matplotlib`, `seaborn` for visualization
  - `scikit-learn` for machine learning

---

## Dataset
Key features include:
- `median_house_value`: Target variable (house price)
- `ocean_proximity`: Categorical feature
- `latitude`, `longitude`: Geographical data
- `total_rooms`, `total_bedrooms`, `population`, `households`: Housing attributes

---

## Workflow

### 1. Data Loading and Splitting
- Split dataset into training (80%) and testing (20%) sets.

### 2. Exploratory Data Analysis (EDA)
- Plotted histograms, heatmaps, and scatterplots to analyze trends.

### 3. Data Preprocessing
- Applied log transformations to reduce skewness.
- One-hot encoded `ocean_proximity`.

### 4. Feature Engineering
- Added:
  - `bedroom_ratio` = total_bedrooms / total_rooms
  - `household_rooms` = total_rooms / households

### 5. Model Training
- **Linear Regression:**
  - Standardized features with `StandardScaler`.
  - Evaluated on test data.
- **Random Forest Regressor:**
  - Optimized using `GridSearchCV` for better performance.

---

## Results
- **Linear Regression:** Basic model.
- **Random Forest Regressor:** Better accuracy after tuning.

---

## Visualizations
- Heatmaps for feature correlations.
- Scatterplots to explore geographic price trends.
- Histograms for feature distributions.

---

## Key Insights
- Proximity to the ocean significantly impacts prices.
- Log transformations improved feature distributions.
- Random Forest outperformed Linear Regression.

---

## How to Use
1. Clone this repository:
   ```bash
   git clone https://github.com/your_username/housing-price-prediction.git
