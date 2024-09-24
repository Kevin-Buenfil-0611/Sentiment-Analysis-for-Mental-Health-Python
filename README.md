# Descripción General

Este proyecto tiene como objetivo clasificar los sentimientos expresados en textos relacionados con la salud mental. Para esto, se utilizan técnicas de procesamiento de lenguaje natural (NLP) y algoritmos de aprendizaje automático que predicen si una declaración tiene un tono positivo, negativo o neutral. El proyecto sigue una arquitectura basada en tres etapas principales: Feature Pipeline, Training Pipeline, y Batch Inference Pipeline.

1. Feature Pipeline Notebook
Esta notebook está diseñada para el preprocesamiento de datos y la ingeniería de características.

Pasos principales:

- Carga de datos: Se utiliza un dataset que contiene textos y sus respectivas etiquetas.
- Limpieza de datos: Se eliminan los valores faltantes y se renombra las columnas para asegurar que los datos estén correctamente estructurados.
- Análisis Exploratorio de Datos (EDA): Se visualiza la distribución de las clases en el dataset.
- Vectorización con TF-IDF: El texto se convierte en representaciones numéricas usando la técnica de TF-IDF, con un límite de 5000 características.
- Ganancia de Información Mutua: Se calcula la ganancia de información para seleccionar las características más relevantes.
- LazyPredict: Se utiliza para comparar diferentes modelos y seleccionar el más adecuado según sus métricas de desempeño (se escoge LGBMClassifier para la siguiente fase).
Almacenamiento de Características: Las características preprocesadas y las etiquetas se guardan en archivos .pkl para su uso posterior.

2. Training Pipeline Notebook
En esta notebook se entrena el modelo de clasificación de sentimientos.

Pasos principales:

- Carga de datos preprocesados: Se cargan los archivos .pkl generados en el Feature Pipeline.
- División de los datos: Se dividen los datos en conjuntos de entrenamiento y prueba.
- Definición del modelo: Se utiliza el algoritmo LGBMClassifier, un modelo de boosting eficiente para tareas de clasificación.
- Entrenamiento del modelo: Se entrena el modelo utilizando los datos de entrenamiento.
- Evaluación del modelo: Se calculan métricas como accuracy y F1 score en el conjunto de prueba.
- Registro en MLFlow: El modelo y las métricas de evaluación se registran utilizando MLFlow para un seguimiento adecuado.
- Guardado del modelo entrenado: El modelo final se guarda en un archivo .pkl para su uso en la etapa de inferencia.

3. Batch Inference Pipeline Notebook
La notebook de inferencia por lotes está diseñada para realizar predicciones en nuevos datos.

Pasos principales:

- Carga del modelo entrenado: Se carga el modelo guardado en la fase de entrenamiento.
- Cargar nuevos datos: Se cargan los nuevos datos para hacer predicciones.
- Realizar predicciones: El modelo realiza predicciones sobre los nuevos datos.
- Almacenamiento de predicciones: Las predicciones se guardan en un archivo para su análisis posterior.

Resultados Esperados

a) Modelo de Clasificación Eficiente: Un modelo basado en LGBMClassifier que es eficiente en términos de velocidad y precisión para la clasificación de sentimientos en textos.

b) Almacenamiento y Registro: Los modelos entrenados y las métricas estarán correctamente registrados en MLFlow, facilitando la trazabilidad y la comparabilidad con otros experimentos.

c) Predicciones por Lotes: Un pipeline funcional para predecir sentimientos en grandes lotes de datos textuales.

Este proyecto puede ser utilizado como base para tareas de clasificación de sentimientos en textos relacionados con salud mental o cualquier otro dominio.

Base de datos empleada en el proyecto: [Kaggle Link](https://www.kaggle.com/datasets/suchintikasarkar/sentiment-analysis-for-mental-health)