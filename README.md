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
   cd your_local_root\API-steel-rebar-price-prediction
2. Crear y activar el entorno virtual
   ```bash
   conda create -n API-steel-rebar-price-prediction_env python=3.11.4 -y
   conda activate API-steel-rebar-price-prediction_env
3. Instalar dependencias
   ```bash
   pip install -r requirements.txt
4. Navegar a 
   your_local_root\API-steel-rebar-price-prediction
   y abrir el archivo
   model_develop_steel_rebar.ipynb en su IDE prefererido, por ejemplo VSCode.

5. Ejecutar el script, indicando adecuadamente el environment previamente creado.

**API**:
1. Abrir una terminal de Anaconda Prompt e ir a la carpeta donde descargaste este proyecto:
   ```bash
   cd your_local_root\API-steel-rebar-price-prediction
2. Crear y activar el entorno virtual
   ```bash
   conda create -n API-steel-rebar-price-prediction_env python=3.11.4 -y
   conda activate API-steel-rebar-price-prediction_env
3. Instalar dependencias
   ```bash
   pip install -r requirements.txt
4. Ejecutar el servidor FastAPI
   uvicorn appFastAPI.app:app --reload
5. Abrir la documentación interactiva (Ver el link en la terminal de Anaconda Prompt) en un navegador web
   Ejemplo: http://127.0.0.1:8000/docs
6. En la API app, seleccionar el endpoint GET, inglesar el API_KEY = deacero-2025 y verá la predicción del precio de la varilla corrugada para el siguiente día:
   
  "prediction_date": "2025-12-31",
  "predicted_price_usd_per_ton": 596.79,
  "currency": "USD",
  "unit": "metric ton",
  "model_confidence": 0.8,
  "timestamp": "2025-12-30T17:23:02.194507Z"
   
 7. **La API REST pública es:** https://api-steel-rebar-price-prediction-13.onrender.com/

**Interpretación de solución para negocio**:

Este proyecto proporciona un modelo predictivo de precios de la varilla corrugada en USD/ton, considerando factores macroeconómicos y materias primas. La interpretación clave para negocio es:

Precio de varilla (rebar_price): Permite anticipar tendencias de costos para planificación de compras y presupuestos de construcción.

Factores de influencia: Precios de acero laminado, mineral de hierro, carbón coquizable, aluminio y cobre; tipo de cambio USD/CNY y USD/MXN; volatilidad del S&P 500 (VIX). Esto ayuda a identificar qué variables macroeconómicas impactan más el precio.

Toma de decisiones: Con predicciones diarias, empresas pueden optimizar inventarios, negociar contratos y gestionar riesgos financieros.

Limitaciones: Algunos datos históricos se cargan desde CSV (Steel_Rebar_Futures_Historical_Data.csv) y no se actualizan automáticamente; otros (Yahoo Finance, FRED) sí se descargan en tiempo real, lo que permite predicciones más recientes y confiables.

Resumen: La herramienta soporta decisiones estratégicas y operativas en compras y planificación financiera, destacando riesgos y oportunidades en el mercado de la varilla corrugada.
