# Conclusiones del Proyecto

## Resumen General

El presente proyecto tuvo como objetivo desarrollar modelos de **clasificación** (predicción de abandono) y **regresión** (predicción del promedio final) utilizando el algoritmo **K-Nearest Neighbors (KNN)** sobre un conjunto de datos real de estudiantes universitarios. A continuación se presentan las principales conclusiones derivadas del análisis exploratorio, la selección de variables y la evaluación de los modelos.

## Principales Hallazgos del Análisis Exploratorio

### Distribución de la Variable Objetivo
- La variable `Target` presentó una distribución **relativamente equilibrada**: 49.9% graduados, 32.1% abandonos y 17.9% matriculados. Esto permitió un modelado de clasificación sin problemas extremos de desbalance.
- Se reclasificó la variable a formato binario (`Graduate` = 0, `Dropout` = 1) para enfocar el análisis en la predicción de deserción.

### Factores Asociados al Abandono
- **Factores financieros** (`Tuition fees up to date`, `Debtor`, `Scholarship holder`) mostraron la asociación más fuerte con el abandono, según las pruebas Chi-Cuadrado.
- El **rendimiento académico** (especialmente unidades aprobadas y calificaciones del segundo semestre) resultó ser el principal discriminante entre estudiantes que abandonan y los que se gradúan.
- Variables como `Nacionality`, `International` y `Educational special needs` no mostraron asociación significativa con el abandono, por lo que fueron excluidas del modelo.

### Factores Asociados al Promedio Final
- Las **calificaciones semestrales** presentaron una correlación casi perfecta con el promedio final (Spearman > 0.94), lo que era esperable dado que la variable objetivo se construyó como el promedio de ambas.
- El `Course` (programa de estudios) resultó ser la variable categórica más relevante para predecir el rendimiento académico, reflejando diferencias en la dificultad entre carreras.

## Rendimiento del Modelo de Clasificación (k = 21)

| Métrica | Valor | Evaluación |
|---------|-------|-------------|
| **Accuracy** | 84.85% | Buen rendimiento general |
| **Precision** | 86.77% | Bajo nivel de falsas alarmas |
| **Recall** | 91.68% | Excelente capacidad para detectar abandonos reales |
| **F1-Score** | 89.15% | Equilibrio óptimo entre precisión y sensibilidad |
| **AUC-ROC** | Alto (no calculado explícitamente) | Buena capacidad discriminante en todos los umbrales |

**Conclusión sobre clasificación:** El modelo es **altamente sensible** (recall = 91.68%), lo cual es fundamental para un sistema de alerta temprana donde el costo de no detectar un abandono real es mucho mayor que el de generar una falsa alarma. La precisión del 86.77% es aceptable y el modelo es **apto para su implementación**.

## Rendimiento del Modelo de Regresión (k = 6)

| Métrica | Valor | Evaluación |
|---------|-------|-------------|
| **R²** | 0.9946 | El modelo explica el 99.46% de la variabilidad |
| **EVS** | 0.9947 | Ausencia de sesgos sistemáticos |
| **MAE** | 0.2208 | Error promedio de menos de un cuarto de punto (escala 0-20) |
| **RMSE** | 0.3556 | Sin errores catastróficos |
| **RMSLE** | 0.0276 | Error porcentual mínimo (~2.8%) |

**Conclusión sobre regresión:** El modelo presenta un **rendimiento sobresaliente**. El alto R² era esperable dado que la variable objetivo se construyó como promedio de variables predictoras. La precisión absoluta (MAE = 0.22) y relativa (RMSLE = 2.8%) lo hacen **altamente confiable** para predecir el promedio final de los estudiantes.

## Ventajas y Limitaciones del Método KNN

### Ventajas identificadas
- **Simplicidad y transparencia:** El algoritmo es fácil de entender e interpretar.
- **No paramétrico:** No asume distribuciones específicas de los datos.
- **Flexibilidad:** Puede usarse tanto para clasificación como para regresión.
- **Robustez con escalamiento adecuado:** El uso de `RobustScaler` mitigó el impacto de outliers.

### Limitaciones identificadas
- **Sensibilidad a la escala de las variables:** Fue necesario aplicar escalamiento exhaustivo.
- **Dependencia de la selección de k:** El rendimiento varía significativamente con el valor de k, requiriendo validación manual.
- **Coste computacional:** Aunque no fue un problema con este dataset, KNN puede ser costoso en datasets muy grandes.
- **Dificultad con alta dimensionalidad:** El proyecto manejó una dimensión moderada, evitando la maldición de la dimensionalidad.

## Conclusiones Finales

- **Para la universidad:** El modelo de clasificación (k=21) puede implementarse como un **sistema de alerta temprana** que identifique a estudiantes en riesgo de abandono, priorizando las variables financieras y de rendimiento académico.

- **Para la predicción de rendimiento:** El modelo de regresión (k=6) es **altamente preciso** y puede utilizarse para estimar el promedio final de los estudiantes, permitiendo intervenciones tempranas.