# CENTRO POLITÉCNICO SUPERIOR MALVINAS ARGENTINAS - APRENDIZAJE AUTOMÁTICO
# Alumna-FERNÁNDEZ, Ana María
# Clase 4 – Regresión Lineal Múltiple (Presión Arterial)

Este repositorio contiene la entrega de la **Clase 4** usando el dataset `dataset_regresion_multiple.csv` (separado por `;`). Se construye y evalúa un **modelo de regresión lineal múltiple** para predecir la **presión arterial**.

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
### Métricas (test)

**Modelo completo (todas las variables)**
- R²: **0.708**
- RMSE: **10.36** mmHg
- MAE: **8.60** mmHg

**Modelo simplificado (Top-3 por |corr|: peso, edad, estrés)**
- R²: **0.652**
- RMSE: **11.31** mmHg
- MAE: **9.55** mmHg

> Conclusión: el **modelo completo** ajusta mejor (↑R², ↓errores). El **Top-3** rinde cerca y es más interpretable, confirmando que **peso, edad y estrés** son los principales factores.


Gráficos (en `figs/`):
- `y_real_vs_pred_regresion_multiple.png`
- `residuales_regresion_multiple.png`

- En el primer gráfico (valores reales vs. predichos) los puntos van subiendo de izquierda a derecha, bastante cerca de la línea imaginaria “perfecta”. Esto dice que el modelo acierta la tendencia general: cuando la presión real es más alta, la predicción también sube. Igual se ve algo de dispersión: a veces el modelo se pasa o se queda corto unos 8–10 mmHg, que es lo que mostraron tus métricas.

- En el histograma de residuales, la mayoría de los errores están cerca de cero y no aparecen valores extremos raros. Hay un poquito más de casos donde el modelo subestima (errores negativos) que donde sobrestima, pero no es algo grave.

> En resumen, el modelo funciona bien para este ejercicio. Capta la relación y comete errores moderados. Si quisieras afinarlo, podrías probar regularización (Ridge) o sumar más datos/variables para reducir esa dispersión.

---

## Conclusiones

- Principales factores: **peso**, **edad** y **estres** explican la mayor parte de la variación en presión arterial.
- **horas_ejercicio** aporta menos que las tres anteriores.
- **ingresos** y **horas_tv**: baja importancia en este dataset.
- El **modelo completo** suele ajustar mejor; el **Top-3** es más interpretable.
- Con **R² ≈ 0.7** y errores **~8–10 mmHg**, el ajuste es razonable para el ejercicio.

---
