# 📉 Module 3 — Customer Churn: Ансамблевые методы

**Автор:** Бреславская Ирина Владимировна, ПКТб-23-1  
**Дата:** 2026-10-19  

## Результаты

| Модель | Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---|---|---|---|---|
| **Random Forest** | 0.7608 | 0.5348 | 0.7594 | 0.6276 | 0.8394 |
| **XGBoost** | 0.7743 | 0.5579 | 0.7219 | 0.6294 | 0.8312 |
| **LightGBM** | 0.7601 | 0.5341 | 0.7540 | 0.6253 | 0.8375 |
| **CatBoost** | 0.7488 | 0.5187 | 0.7433 | 0.6110 | 0.8409 |
| **Stacking (Бонус)** | **0.7977** | **0.6344** | 0.5615 | 0.5957 | **0.8424** |

**Анализ результатов:**
- **Лучшие модели по ROC-AUC:** Среди базовых алгоритмов лидируют `CatBoost` (`0.8409`) и `Random Forest` (`0.8394`), а ансамбль `Stacking` достигает `0.8424`.
- **Скорость работы:** `LightGBM` обучается быстрее всех остальных моделей (`~0.071 сек`), в 3 раза опережая `XGBoost` и в 6 раз — `CatBoost`.
- **Соотношение Precision и Recall:** В базовых моделях с взвешенными классами (`class_weight='balanced'`) `Recall` составляет `74–78%`, что позволяет находить подавляющее большинство реально уходящих клиентов, тогда как в `Stacking` со стандартным порогом `0.5` `Precision` выше `Recall` (`0.6595` против `0.5481`) — мета-модель осторожнее выдаёт метку «уйдёт».
- **Бизнес-порог:** Смещение порога классификации с учётом матрицы стоимости (`FN = 5`, `FP = 1`) дополнительно снижает суммарные финансовые потери оператора.

```
├── module-3-churn/
│   ├── README.md
│   ├── notebook.ipynb
│   ├── data/
│   │   ├── telco_churn.csv
│   │   └── churn_info.md
│   ├── models/
│   │   ├── best_model.pkl
│   │   ├── rf_model.pkl
│   │   ├── xgb_model.pkl
│   │   ├── lgbm_model.pkl
│   │   ├── cat_model.pkl
│   │   ├── scaler.pkl
│   │   ├── feature_cols.json
│   │   ├── label_encoders.pkl
│   │   └── metrics.json
│   ├── examples/
│   │   ├── eda_plots.png
│   │   ├── feature_importance.png
│   │   ├── shap_summary.png
│   │   ├── shap_waterfall.png
│   │   └── roc_curves.png
│   └── requirements.txt
```

## Быстрый старт

```python
import joblib
import requests
from io import BytesIO

BASE_URL = "https://raw.githubusercontent.com/breslavskayaira/ml-course-breslavskaya/main/module-3-churn"
model = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/best_model.pkl").content))
feature_cols = requests.get(f"{BASE_URL}/models/feature_cols.json").json()