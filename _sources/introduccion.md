# Información del Proyecto

El presente proyecto se enmarca en el desafío que enfrentan las instituciones de educación superior para anticipar y mitigar el **abandono académico**, un fenómeno que afecta tanto la trayectoria de los estudiantes como la eficiencia del sistema educativo. Con el objetivo de contribuir a la solución de este problema, se desarrollan modelos de **aprendizaje automático supervisado** utilizando el algoritmo de **K-Vecinos Más Cercanos (K-Nearest Neighbors, KNN)** para dos tareas fundamentales:

1.  **Clasificación binaria:** Estimar la probabilidad de que un estudiante abandone sus estudios.
2.  **Regresión continua:** Predecir el índice acumulado esperado (promedio de calificaciones) al final del semestre.

## Contexto y Dataset

El proyecto se basa en el conjunto de datos **"Predict Students’ Dropout and Academic Success"**, disponible en el repositorio público de la Universidad de California, Irvine (UCI) con el identificador `697`. Este dataset, creado a partir de registros reales de una institución de educación superior portuguesa, contiene información de **4,424 estudiantes** matriculados en diversas titulaciones de grado, como enfermería, gestión, agronomía, diseño y comunicación, entre otras.

La riqueza del dataset radica en que integra tres tipos de variables para cada estudiante, permitiendo un análisis multidimensional del fenómeno de la deserción:

*   **Variables demográficas y socioeconómicas:** Edad al matricuarse, nacionalidad, género, estado civil, nivel educativo y ocupación de los padres, situación financiera (deudor, becario, matrícula al día).
*   **Variables académicas previas:** Vía de acceso (nota de admisión, titulación previa, modalidad y orden de solicitud).
*   **Variables de rendimiento durante el curso:** Calificaciones, unidades curriculares aprobadas, inscritas, evaluadas, acreditadas y sin evaluar, tanto para el primer como para el segundo semestre.

El dataset se destaca por no presentar valores faltantes, lo que facilita su procesamiento, y porque su variable objetivo (`Target`) incluye tres estados al final de la duración normal del curso: **"Graduate"** (graduado), **"Dropout"** (abandono) y **"Enrolled"** (aún matriculado). Esta composición permite formular el problema como una tarea de clasificación multiclase, aunque en este proyecto se reformulará como una tarea binaria (abandono vs. no abandono) para enfocarse en la predicción del riesgo de deserción.

## Estructura del Proyecto

El desarrollo del proyecto sigue una secuencia metodológica rigurosa, documentada en este cuaderno (notebook), que incluye las siguientes fases:

1.  **Análisis Exploratorio de Datos (EDA):** Se examinan las distribuciones, frecuencias y relaciones entre las variables para comprender la estructura subyacente de los datos e identificar posibles patrones o sesgos.
2.  **Preprocesamiento:** Se aplican técnicas de limpieza, codificación de variables categóricas (One-Hot Encoding), reducción de categorías poco frecuentes, y normalización/escalado de variables numéricas (utilizando `RobustScaler` para mitigar el impacto de valores atípicos).
3.  **Selección de Características (Feature Selection):** Mediante pruebas estadísticas como Chi-Cuadrado (para variables categóricas frente a la clasificación) y Kruskal-Wallis (para variables numéricas frente a la regresión), se identifican las variables más relevantes para cada modelo, optimizando su rendimiento y evitando el sobreajuste.
4.  **Modelado KNN:** Se implementan dos modelos KNN:
    *   **Clasificación:** Para predecir el abandono, evaluando múltiples valores de `k` (número de vecinos) y seleccionando el óptimo mediante validación cruzada manual (respetando las restricciones didácticas de no usar `GridSearchCV`). Se aborda el desbalance de clases con la técnica de sobremuestreo SMOTE.
    *   **Regresión:** Para predecir el promedio final, utilizando los valores de `k` que minimizan el error relativo (RMSLE).
5.  **Evaluación y Comparación:** Cada modelo se evalúa con métricas apropiadas para su tarea (matriz de confusión, precisión, recall, F1-score y curva ROC para clasificación; R², MAE, RMSE y RMSLE para regresión). Finalmente, se contrastan los resultados de ambos modelos y se reflexiona sobre las ventajas y limitaciones del método KNN en este contexto real.

## Consideraciones Finales

A través de este proyecto, se busca no solo construir modelos predictivos con buen rendimiento, sino también **comprender qué factores influyen en el abandono** y en el rendimiento académico. Los resultados obtenidos permitirán responder preguntas clave como: ¿Qué variables financieras o académicas son las más determinantes para predecir la deserción? ¿Es más fácil predecir el abandono o el promedio final? ¿Qué valor de `k` ofrece el mejor compromiso entre sesgo y varianza en cada caso?

Las secciones que siguen presentan de manera detallada cada etapa del análisis, desde la exploración inicial de los datos hasta la evaluación final de los modelos. El proyecto concluye con una reflexión sobre las **ventajas y limitaciones del método KNN** en contextos educativos reales, ofreciendo recomendaciones prácticas para su posible implementación en sistemas de alerta temprana.