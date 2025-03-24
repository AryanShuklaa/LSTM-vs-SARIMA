# **Revenue Forecasting Using SARIMA and LSTM**

## **Overview**
This project compares two forecasting models—**SARIMA** and **LSTM**—to predict revenue trends using historical marketing spend and impression data. The dataset used for training is `Forecasting_data.xlsx`, which includes multiple features like spend across different platforms and impressions.

## **Project Structure**
```
|── Forecasting_data.xlsx   # Dataset used for training & testing
|── forecasting.ipynb       # Jupyter Notebook with SARIMA & LSTM models
|── README.md               # Project documentation
|── requirements.txt        # List of dependencies
```

## **Setup Instructions**
### **1. Clone the Repository**
```sh
git clone <repository_link>
cd <repository_name>
```
### **2. Create a Virtual Environment**
```sh
python -m venv venv
source venv/bin/activate  # On Mac/Linux
venv\Scripts\activate     # On Windows
```
### **3. Install Dependencies**
```sh
pip install -r requirements.txt
```

## **Data Preprocessing**
- Read data from `Forecasting_data.xlsx` and handle missing values.
- Split data into training (80%) and testing (20%).
- Normalize the data using `MinMaxScaler`.

## **Model Implementation**
### **SARIMA Model**
- Order: `(1,1,1)`
- Seasonal Order: `(1,1,1,4)`
- Uses external regressors (`spend_meta`, `spend_google`, etc.)
- Generates future forecasts using learned patterns.

### **LSTM Model**
- Uses `Sequential` model with:
  - **LSTM layer** (64 units, ReLU activation)
  - **Dropout** (0.2)
  - **Dense layer** (1 output)
- Uses **time series sliding window** approach (`time_steps = 4`).

## **Evaluation Metrics**
Both models are evaluated using:
- **Mean Absolute Error (MAE)**
- **Root Mean Squared Error (RMSE)**
- **R² Score**

### **Results**
| Model  | MAE  | RMSE  | R² Score |
|--------|------|-------|---------|
| SARIMA | 21.81 | 27.78 | 0.55    |
| LSTM   | 29.93 | 37.13 | 0.20    |

SARIMA performs better in this case.

## **Visualization**
- **Forecast comparison plot** (`matplotlib`)
- **Error metric comparison (bar chart)**

## **Future Improvements**
- Fine-tuning hyperparameters for better results.
- Exploring hybrid models (SARIMA + LSTM).


