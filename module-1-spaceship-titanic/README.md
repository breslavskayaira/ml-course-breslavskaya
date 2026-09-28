# EDA и бинарная классификация на датасете "Spaceship Titanic"

**Автор:** Бреславская Ирина, ПКТб-23-1  
**Дата:** 2026-09-29  
**Датасет:** Spaceship Titanic

## Результаты

| Модель | Accuracy | Precision | Recall | F1 | ROC-AUC |
|--------|----------|-----------|--------|----|---------|
| Logistic Regression | 0.7941 | 0.7878 | 0.8094 | 0.7984 | 0.8816 |
| Decision Tree | 0.7878 | 0.7924 | 0.7842 | 0.7883 | 0.81 |

**Время обучения:** LR ≈ 0.007 сек, DT ≈ 0.013 сек

## Быстрый старт

```python
import joblib
import requests
from io import BytesIO

BASE_URL = "https://raw.githubusercontent.com/breslavskayaira/ml-course-breslavskaya/main/module-1-spaceship-titanic"
model = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/lr_model.pkl").content))
scaler = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/scaler.pkl").content))
features = requests.get(f"{BASE_URL}/models/feature_cols.json").json()
