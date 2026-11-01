# 🛒 Module 4 — Online Shoppers: Инженерия признаков

**Автор:** Бреславская Ирина, ПКТб-23-1
**Дата:** 2026-11-01

## Результаты

| Модель | Accuracy | Precision | Recall | F1 | ROC-AUC | Время |
|--------|----------|-----------|--------|-----|---------|-------|
| Random Forest | 0.8686 | 0.5511 | 0.8194 | 0.6589 | 0.9290 | 0.273 сек |
| XGBoost | 0.88 | 0.8812 | 0.5965 | 0.7199 | 0.6524 | 0.9241 сек |
| LightGBM | 0.88 | 0.8767 | 0.5756 | 0.7775 | 0.6615 | 0.9272 сек |
| CatBoost | 0.87 | 0.8666 | 0.5481 | 0.7906 | 0.6474 | 0.9265 сек |
| **LightGBM (Optuna)** | **0.88** | **0.8767** | **0.5756** | **0.7775** | **0.6615** | — |

**Лучшая модель:** LightGBM (Optuna) (ROC-AUC = 0.93)
**Время обучения:** < 0.30 сек на базовую модель LightGBM

## Быстрый старт

```python
import joblib
import requests
from io import BytesIO

BASE_URL = "[https://raw.githubusercontent.com/breslavskayaira/ml-course-breslavskaya/main/module-4-features](https://raw.githubusercontent.com/breslavskayaira/ml-course-breslavskaya/main/module-4-features)"
model = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/best_model.pkl").content))
scaler = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/scaler.pkl").content))
features = requests.get(f"{BASE_URL}/models/feature_cols.json").json()
```

## Структура
- `notebook.ipynb` — полный отчёт (14 разделов)
- `models/` — 5 моделей, скейлер и метаданные
- `data/` — датасет `online_shoppers_intention.csv` и описание `dataset_info.md`
- `examples/` — графики EDA, ROC-кривые, Feature Importance и SHAP
- `requirements.txt` — список библиотек