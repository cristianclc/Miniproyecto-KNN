# Predicción de Abandono Académico y Rendimiento Estudiantil

## Descripción del Proyecto

Este proyecto aborda el problema del abandono académico en educación superior mediante el uso de técnicas de aprendizaje automático supervisado, específicamente el algoritmo K-Nearest Neighbors (KNN).

Se desarrollan dos modelos principales:

- **Clasificación binaria:** Predicción del riesgo de deserción estudiantil.
- **Regresión:** Estimación del promedio académico final del estudiante.

El enfoque integra un flujo completo de ciencia de datos, desde el análisis exploratorio hasta la evaluación rigurosa de modelos, con énfasis en interpretabilidad y aplicación en contextos reales.

## Colaboradores

- Cristian Linero
- David Márquez

## Dataset

- **Nombre:** Predict Students’ Dropout and Academic Success  
- **Fuente:** UCI Machine Learning Repository  
- **ID:** 697  
- **Origen:** Institución de educación superior en Portugal
- **Enlace:** https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success

## Objetivos

### Objetivo General

Desarrollar modelos predictivos utilizando KNN para identificar estudiantes en riesgo de abandono y estimar su rendimiento académico.

### Objetivos Específicos

1. Realizar análisis exploratorio de datos (EDA)
2. Preprocesar datos (encoding, escalado, limpieza)
3. Aplicar selección de características
4. Implementar modelos KNN para:
   - Clasificación
   - Regresión
5. Optimizar hiperparámetro `k` manualmente
6. Evaluar desempeño de los modelos
7. Analizar variables más influyentes

## Metodología

El proyecto sigue una estructura clara:

1. Análisis Exploratorio (EDA)
2. Preprocesamiento
   - One-Hot Encoding
   - Escalado con `RobustScaler`
3. Selección de Características
   - Chi-cuadrado
   - Kruskal-Wallis
4. Modelado con KNN
5. Optimización de `k`
6. Evaluación
7. Interpretación de resultados
