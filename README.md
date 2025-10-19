# 30-Day Bitcoin Price Forecasting Data Pipeline

---

### **Cryptocurrency Time Series Analysis: BTC Feature Engineering**

This Jupyter Notebook implements the crucial **data preparation and feature engineering** steps for a Bitcoin (BTC) price forecasting model. The focus is on preparing daily price data and correctly creating the **prediction target** for a 30-day outlook.

#### **The Core Challenge: Generating the Future Target**

The key function of this notebook is to transform the time series problem into a **supervised learning problem**:

* **Goal:** Predict the price 30 days from today.
* **Method:** The **`Prediction`** target column is created by shifting the original `Price` data by **30 rows up** (using `df['Price'].shift(-30)`).
* This links a row of features (current price) to the value that actually occurred 30 days later, making it the ground truth for the model to learn.

#### **Data and Key Preparation Steps**

| Component                | Description                                                                                            |
| :----------------------- | :----------------------------------------------------------------------------------------------------- |
| **Input Data**     | **`bitcoin.csv`** (daily `Date` and `Price`)                                               |
| **Feature (X)**    | The**`Price`** column (current day's closing price)                                            |
| **Target (y)**     | The**`Prediction`** column (the price from 30 days in the future)                              |
| **Cleaning Focus** | Dropping the non-numerical**`Date`** column and handling the last 30 **`NaN`** values. |

---

### **Notebook Execution Flow**

This dynamic pipeline ensures the final arrays are ready for immediate model training (e.g., using scikit-learn or TensorFlow):

1. **Libraries & Load:** Import `pandas` and `numpy` and `scikit-learn`. Load **`bitcoin.csv`** into a DataFrame.
2. **Date Cleanup:** The non-numeric `Date` column is removed.
3. **Target Creation:** The **`Prediction`** column is engineered using `df['Price'].shift(-30)`.
4. **Data Trimming:** Rows containing the `NaN` values at the end of the newly created `Prediction` column are dropped, as the 30-day future price is unknown for those entries.
5. **Final Array Prep:** The feature data (**`X`**) and the target data (**`y`**) are converted to `numpy` arrays, ensuring they are perfectly aligned and ready for the next step of model training.

### **Quick Setup Guide**

1. **Clone/Download:** Get the notebook and your `bitcoin.csv` file.
2. **Dependencies:** Ensure you have the core libraries:
   ```bash
   pip install pandas numpy scikit-learn
   ```
3. **Run:** Execute the cells sequentially in Jupyter to generate your prepared feature and target datasets (`X` and `y`).
