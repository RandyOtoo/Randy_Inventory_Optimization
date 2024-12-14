# Randy_Inventory_Optimization



## Inventory Optimization Using Machine Learning and Deep Learning
Efficient inventory management is essential for businesses aiming to reduce holding costs, prevent stockouts, and optimize their operations. This project employs advanced machine learning and deep learning techniques to analyze and forecast inventory needs using datasets comprising purchase prices, sales transactions, inventory levels, and supplier information. By calculating and applying inventory-specific Key Performance Indicators (KPIs) such as Optimal Order Quantity (EOQ), Safety Stock, and Reorder Points (ROP), this project offers data-driven solutions to maintain optimal stock levels and improve supplier coordination.



## Project Overview
The primary objective of this project is to develop a predictive model that optimizes inventory management by accurately forecasting demand using Machine Learning and Deep Learning techniques. 


Demand Forecasting: Predicting future demand using deep learning models such as LSTM for accurate stock adjustments.

Optimization: Implementing replenishment strategies to minimize costs while maintaining service levels.

### Key  Performance Indicators (KPIs)
Optimal Order Quantity (EOQ)
Definition: The Economic Order Quantity (EOQ) is the ideal order quantity a company should purchase to minimize its total inventory costs, including ordering costs and holding costs.

Inventory Turnover Ratio (ITR)
Measures how efficiently inventory is used over a specific period:

Safety Stock (SS)
Ensures protection against demand variability during lead time.

Reorder Point (ROP)
The inventory level at which a new order should be placed:

Holding Cost (HC)
Reflects the cost of storing unsold inventory:


## Demand Forecasting with Deep Learning
Using historical sales data, a Long Short-Term Memory (LSTM) model was trained to forecast future demand. The model captures temporal dependencies, seasonality, and trends, offering a robust prediction framework. The pipeline includes:

Data Preprocessing: Time series normalization and handling missing values. Created sequence for LSTM model.


Model Architecture: 

A multi-layer LSTM network with two LSTM layers: the first with 128 units and return_sequences=True, followed by a dropout layer with a rate of 0.3, and the second LSTM with 64 units and return_sequences=False, followed by another dropout layer. After the LSTMs, it has two dense layers: one with 50 units and relu activation, and a final output layer with 1 unit for regression. The total number of trainable parameters in the model is 119,269.

Evaluation Metrics: Metrics like Mean Squared Error (MSE) , Root Mean Squared Error (RMSE) and Mean Absolute Error(MAE) are used to evaluate the accuracy of forecasts.


## Insights 

Linear Regression and Random Forest Models:
Both models have very low MAE, MSE, and RMSE values (e.g., RMSE ~ 8.6), coupled with an exceptionally high R² score (0.99), indicating strong predictive accuracy.
These models are simple, interpretable, and highly effective for the given dataset. They may perform well in scenarios where demand trends and seasonality are straightforward.

ARIMA Model:
ARIMA shows significantly higher errors compared to other models (e.g RMSE > 1000). This indicates that ARIMA might not be the best choice for this dataset, possibly due to complex patterns that ARIMA struggles to capture. It may work better with preprocessed or detrended data and in scenarios with a strong, well-defined seasonality.

LSTM Model:
The LSTM model has much higher errors (e.g RMSE ~ 1002) than Linear Regression and Random Forest, despite its suitability for time series forecasting.
The LSTM likely underperformed due to insufficient tuning, inadequate data preprocessing (e.g., handling outliers or seasonality), or not enough data to effectively train a deep learning model.


## Recommendations

Demand Forecasting:

Use Random Forest or Linear Regression for short-to-medium-term demand forecasting as they balance simplicity and accuracy well.
Investigate why ARIMA and LSTM underperformed. For ARIMA, I must ensure to find the optimal orders(p,d,q).  For LSTM, I may have to consider feature engineering, more training data, or hyperparameter tuning.

Inventory Optimization:

Use highly accurate models like Random Forest or Linear Regression to predict demand and adjust inventory levels to minimize overstocking or understocking.
Combine forecast outputs with inventory management techniques like safety stock calculations and reorder points.


## Future Work: 
Optimize Hyperparameters: Use grid search or random search to find the optimal hyperparameters such as the number of layers, neurons per layer, learning rate etc.

Incorporate Additional Features: Include more features such as holiday effects, promotional events, weather conditions.
 
External Data Sources: Integrate external data such as macroeconomic indicators, market trends, and social media sentiment to enrich the model's input.


