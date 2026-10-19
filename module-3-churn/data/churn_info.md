# Telco Customer Churn — Описание датасета

**Источник:** https://www.kaggle.com/datasets/blastchar/telco-customer-churn

**Структура:**
- Всего примеров: 7043
- Признаков: 19 (+ `customerID` + целевая `Churn`)
- Числовых признаков: 3 (`tenure`, `MonthlyCharges`, `TotalCharges`)
- Категориальных признаков: 16 (4 демографических, 9 признаков подключённых услуг, 3 категориальных признака аккаунта)

**Описание ключевых столбцов:**

| Столбец | Тип | Описание | Пропуски |
|---|---|---|---|
| `customerID` | object | Уникальный ID клиента | 0% |
| `gender` | object | Пол клиента (`Male` / `Female`) | 0% |
| `SeniorCitizen` | int (0/1) | Пенсионер (`1` — да, `0` — нет) | 0% |
| `tenure` | int | Количество месяцев с компанией (0–72) | 0% |
| `InternetService` | object | Тип интернета (`DSL`, `Fiber optic`, `No`) | 0% |
| `Contract` | object | Тип контракта (`Month-to-month`, `One year`, `Two year`) | 0% |
| `MonthlyCharges` | float | Ежемесячная плата ($) | 0% |
| `TotalCharges` | object | Общая сумма платежей ($) | ~0.2% (11 пробелов) |
| `Churn` | object | **Целевая переменная** (`Yes` / `No`) | 0% |

**Распределение классов:**
- `No` (остался): 5174 (73.5%)
- `Yes` (ушёл): 1869 (26.5%)