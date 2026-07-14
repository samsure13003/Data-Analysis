# ✈️ Flight Price Prediction — EDA & Feature Engineering

Exploratory Data Analysis and feature engineering pipeline on a real-world Indian flight fare dataset, preparing raw booking data for machine learning-based price prediction.

## 📌 Overview

This project takes a messy, real-world flight booking dataset (10,683 rows) and transforms it into a clean, fully numeric, model-ready format. It covers the full journey from raw string-based date/time fields to one-hot encoded categorical features, with EDA performed at each step to understand the underlying data.

## 📂 Dataset

| | |
|---|---|
| **File** | `flight_price.xlsx` |
| **Rows** | 10,683 |
| **Columns** | 11 |
| **Target** | `Price` |

**Original columns:**

| Column | Description |
|---|---|
| `Airline` | Airline operating the flight |
| `Date_of_Journey` | Date of travel (DD/MM/YYYY) |
| `Source` | Departure city |
| `Destination` | Arrival city |
| `Route` | Flight path (e.g. `BLR → DEL`) |
| `Dep_Time` | Departure time |
| `Arrival_Time` | Arrival time (sometimes includes date) |
| `Duration` | Flight duration (e.g. `2h 50m`) |
| `Total_Stops` | Number of stops |
| `Additional_Info` | Extra info (meal, baggage, etc.) |
| `Price` | Ticket price (target variable) |

## 🛠️ What This Notebook Does

**1. Initial Exploration**
- `df.head()`, `df.tail()`, `df.info()`, `df.describe()` to understand structure, types, and summary statistics.

**2. Date & Time Feature Engineering**
- Split `Date_of_Journey` into `Date`, `Month`, `Year` and cast to integers.
- Parsed `Arrival_Time` and `Dep_Time` into separate hour/minute integer columns.
- Extracted `Duration_Hour` and `Duration_Minute` from the free-text `Duration` field using regex.
- Dropped original raw date/time columns after extraction.

**3. Categorical Cleanup**
- Handled missing values in `Total_Stops` using mode imputation.
- Mapped `Total_Stops` to ordinal integers (`non-stop` → 0, `1 stop` → 1, ... `4 stops` → 4).
- Dropped the `Route` column (redundant with `Source`/`Destination`).
- Normalized `Additional_Info` text (lowercased, stripped whitespace).

**4. Encoding**
- Applied `OneHotEncoder` (scikit-learn) to `Airline`, `Source`, `Destination`, and `Additional_Info`.
- Concatenated encoded features back into the main dataframe, producing a fully numeric dataset ready for modeling.

## 🧰 Tech Stack

- **Python 3**
- `pandas`, `numpy` — data manipulation
- `matplotlib`, `seaborn` — visualization
- `scikit-learn` — one-hot encoding

## 🚀 Getting Started

```bash
git clone <repo-url>
cd flight-price-eda
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl
jupyter notebook Flight_price_EDA.ipynb
```

## 📁 Project Structure

```
├── flight_price.xlsx          # Raw dataset
├── Flight_price_EDA.ipynb     # EDA & feature engineering notebook
└── README.md
```

## 🔮 Next Steps

- Train/test split on the processed dataset
- Baseline regression models (Linear Regression, Random Forest, XGBoost)
- Hyperparameter tuning and evaluation (RMSE, R²)
- Feature importance analysis

## 📄 License

This project is open-sourced under the MIT License.
