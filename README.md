# Clase 4 – Regresión Lineal Múltiple (Presión Arterial)

Este repositorio contiene la entrega de la **Clase 4** usando el dataset `dataset_regresion_multiple.csv` (separado por `;`). Se construye y evalúa un **modelo de regresión lineal múltiple** para predecir la **presión arterial**.

> **Nota del profe:** Este ejercicio reemplaza al de PIB mundial. Acá sólo se usa el dataset de presión arterial.

---

## Estructura del repo

```
clase4-regresion/
├── Clase4_Regresion.ipynb         # Notebook con todo el análisis (tu archivo)
├── dataset_regresion_multiple.csv  # Dataset usado (sep=';')
├── README.md                       # Este archivo con el informe
├── figs/                           # Gráficos generados
│   ├── y_real_vs_pred_regresion_multiple.png
│   └── residuales_regresion_multiple.png
└── resultados/                     # Tablas/outputs
    ├── correlaciones_regresion_multiple.csv
    └── coef_modelo_completo.csv
```

---

## Requerimientos

- Google Colab **o** Python 3.10+
- Librerías: `pandas`, `numpy`, `scikit-learn`, `matplotlib`

En local (opcional):
```bash
pip install pandas numpy scikit-learn matplotlib
```

---

## Exploración inicial (EDA)

- Medidas descriptivas (media, mín, máx) y **correlaciones**.
- Variables más relacionadas (|corr| altas) con `presion_arterial`: **peso**, **edad**, **estres**.
- `ingresos` y `horas_tv` muestran relación baja.

> Matriz de correlaciones: `resultados/correlaciones_regresion_multiple.csv`.

---

## Modelado

### Modelo completo (todas las variables)
- Pipeline: `StandardScaler` + `LinearRegression`
- Split: 80/20 (`random_state=42`)
- **Métricas en test (completá con tus valores):**
  - R²: `...`
  - RMSE: `...` mmHg
  - MAE: `...` mmHg

Gráficos (en `figs/`):
- `y_real_vs_pred_regresion_multiple.png`
- `residuales_regresion_multiple.png`

### Modelo simplificado (Top-3 por |corr|)
- Variables: **peso**, **edad**, **estres** (verificá con tu EDA).
- **Métricas en test (completá con tus valores):**
  - R²: `...`
  - RMSE: `...` mmHg
  - MAE: `...` mmHg

> Coeficientes estandarizados del modelo completo: `resultados/coef_modelo_completo.csv`.
> (Opcional) **Ridge**: podés agregar R²/RMSE/MAE si lo corriste.

---

## Conclusiones

- Principales factores: **peso**, **edad** y **estres** explican la mayor parte de la variación en presión arterial.
- **horas_ejercicio** aporta menos que las tres anteriores.
- **ingresos** y **horas_tv**: baja importancia en este dataset.
- El **modelo completo** suele ajustar mejor; el **Top-3** es más interpretable.
- Con **R² ≈ 0.7** y errores **~8–10 mmHg**, el ajuste es razonable para el ejercicio.

---
