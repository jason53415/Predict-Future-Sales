# Predict-Future-Sales
Feature Extraction 與 Model Training 的部份主要參考自 [Feature engineering, xgboost](https://www.kaggle.com/dlarionov/feature-engineering-xgboost)

## Feature Extraction

### Jupyter Notebook:
- [Feature Extraction]()

### Methods
- Lag feature 的部份從前 1, 2, 3, 6, 12 月調整為前 1-6 個月，因此最終多保留了 date_block_num 6-11 的訓練資料沒有被捨棄。
- Trend feature 保留了前 1-6 月完整的變化資訊，並且多求取了二階的變化資訊。
- Last/first sale feature 調整了原始不合理的求取過程。

## Model Training

### Jupyter Notebook:
- [All Months Validation & All Features]()
- [All Months Validation & Selected Features]()
- [Last Month Validation & All Features]()
- [Last Month Validation & Selected Features]()

### Methods
- 使用 XGBoost Regressor 作為主要的訓練模型

- Validation 方式分為兩種：
  - 只取最後一個月作為 validation set
  - 從所有月份的訓練資料中隨機取 20% 作為 validation set

- Feature 的選擇分兩種：
  - Feature Extraction 中得到的所有 features
  - 經由 XGBoost 所給出的 feature importance 手動挑選出的 features
  
## Ensemble

### Jupyter Notebook:
- [Ensemble]()

### Methods
- 依據各個 model 的表現，將所有 model 的預測結果依一定的權重相互加總。
