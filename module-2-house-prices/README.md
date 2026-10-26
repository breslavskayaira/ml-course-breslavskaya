# Module 2 — House Prices: предобработка и регрессия

**Автор:** Бреславская Ирина, ПКТб-23-1
**Дата:** 2026-10-13

## Результаты

| Модель | RMSE (log) | MAE (log) | R² | RMSE ($) |
|--------|-----------|-----------|-----|---------|
| Linear Regression | 0.135 | 0.095 | 0.88 | $28 000 |
| Ridge | 0.128 | 0.090 | 0.90 | $26 000 |
| Lasso | 0.125 | 0.088 | 0.91 | $25 000 |
| ElasticNet | 0.126 | 0.089 | 0.91 | $25 500 |

**Лучшая модель:** Lasso (R² = 0.91)
**Время обучения:** < 0.02 сек на модель

```
├── module-2-house-prices/
│   ├── README.md
│   ├── notebook.ipynb
│   ├── data/
│   │   ├── test.csv
│   │   ├── train.csv
│   │   └── house_prices_info.md
│   ├── models/
│   │   ├── enet_model.pkl
│   │   ├── lasso_model.pkl
│   │   ├── ridge_model.pkl
│   │   ├── lr_model.pkl
│   │   ├── scaler.pkl
│   │   ├── feature_cols.json
│   │   └── metrics.json
│   ├── examples/
│   └── requirements.txt
```

## Быстрый старт

```python
import joblib
import requests
from io import BytesIO

BASE_URL = "https://raw.githubusercontent.com/breslavskayaira/ml-course-breslavskaya/main/module-2-house-prices"
model = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/lasso_model.pkl").content))
scaler = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/scaler.pkl").content))
features = requests.get(f"{BASE_URL}/models/feature_cols.json").json()