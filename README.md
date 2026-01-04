## Data Science Project: Modelado predictivo para predicción de variable continua (regresión) usando una base de datos compuesta por 20 variables continuas.
________________________________________
**Objetivo**

El objetivo de este proyecto es desarrollar un modelo de regresión que pueda:
1) Predecir el valor de una variable target continua.
 ________________________________________
**Base de datos**

Para este proyecto, se usó dos conjunto de datos:
1) Datos de Training: 20 variables continuas y una variable target continua
2) Datos de Test: 20 variables continuas

| Variable | Descripción |
|---------|-------------|
| **feature_0** | Ninguna |
| **feature_1** | Ninguna |
| **feature_2** | Ninguna |
| **feature_3** | Ninguna |
| **feature_4** | Ninguna |
| **feature_5** | Ninguna |
| **feature_6** | Ninguna |
| **feature_7** | Ninguna |
| **feature_8** | Ninguna |
| **feature_9** | Ninguna |
| **feature_10** | Ninguna |
| **feature_11** | Ninguna |
| **feature_12** | Ninguna |
| **feature_13** | Ninguna |
| **feature_14** | Ninguna |
| **feature_15** | Ninguna |
| **feature_16** | Ninguna |
| **feature_17** | Ninguna |
| **feature_18** | Ninguna |
| **feature_19** | Ninguna |
| **target** | Ninguna |
________________________________________
**Solución**

Nuestra solución consistió principalmente en:

1. Calidad de datos, analisis de datos exploratorio, pre-procesamiento de datos, entrenamiento y evaluación de tres modelos de regresión (ElasticNet, RandomForestRegressor y XGBRegressor) para predecir la variable continua target **target**.

La estructura de este proyecto es:

```text

multivariate-regression-blind-test                     # Carpeta de proyecto
│   .gitignore
│   LICENSE
│   ML Modelling Challenge.pdf
│   model_develop_regression.ipynb                     # Python Notebook de analisis y prueba de modelo
│   predictions_blind_test.csv                         # Archivo de salida de predicciones
│   preprocessing_pipeline.pkl                         # Archivo de salida .pkl de preprocesamiento para datos en producción
│   README.md
│   requirements.txt
│   xgb_bestmodel.pkl                                  # Archivo de salida .pkl de mejor modelo ML                             
│
└───data
        blind_test_data.csv                            # Datos de evaluación (sin target)
        training_data.csv                              # Datos de entrenamiento

```

________________________________________
**Ejecución de Solución**

**Análisis**:
1. Abrir una terminal de Anaconda Prompt e ir a la carpeta donde descargaste este proyecto:
   ```bash
   cd your_local_root\multivariate-regression-blind-test
2. Crear y activar el entorno virtual
   ```bash
   conda create -n multivariate-regression-blind-test_env python=3.11.4 -y
   conda activate multivariate-regression-blind-test_env
3. Instalar dependencias
   ```bash
   pip install -r requirements.txt
4. Navegar a 
   your_local_root\multivariate-regression-blind-test
   y abrir el archivo
   model_develop_regression.ipynb en su IDE prefererido, por ejemplo VSCode.

5. Ejecutar el script, indicando adecuadamente el environment previamente creado.

**Interpretación de resultados: Selección de modelo**:

## Resultados de Modelos

| Modelo       | R²_train_CV | RMSE_train_CV | MAE_train_CV | MAPE_train_CV (%) | R²_test | RMSE_test | MAE_test | MAPE_test (%) |
|-------------|-------------|---------------|--------------|------------------|---------|-----------|----------|----------------|
| XGBoost     | 0.838310    | 2.075517      | 1.633324     | 15.934728        | 0.850974| 1.829158  | 1.470710| 11.415850      |
| RandomForest| 0.754542    | 2.557253      | 2.010935     | 20.755130        | 0.771400| 2.265474  | 1.841662| 14.360814      |
| ElasticNet  | 0.680622    | 2.917007      | 2.232953     | 21.498220        | 0.693004| 2.625348  | 2.115523| 15.781392      |

Dado que se observo: 

- Máximo desempeño en R²_test (~0.85) con XGBoost.
- Menores errores (RMSE, MAE, MAPE) comparado con otros modelos.
- Buen equilibrio entre entrenamiento y prueba, indicando bajo overfitting.
- Capacidad para capturar relaciones no lineales complejas.

XGBoost fue seleccionado como el modelo final para entrenamiento completo y despliegue en datos no vistos.


**Interpretación de resultados en conjunto de datos nuevos (blind_test)**:


