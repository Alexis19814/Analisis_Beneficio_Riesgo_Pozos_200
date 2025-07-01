# Analisis_Beneficio_Riesgo_Pozos_200

🧭 1. Definición del problema
Objetivo: Predecir el volumen de reservas en pozos nuevos y seleccionar la región más rentable con bajo riesgo.

Restricciones:

Solo se permite regresión lineal.

Se deben seleccionar los 200 pozos con mayor volumen estimado por región.

El riesgo de pérdida debe ser < 2.5%.

El ingreso mínimo por pozo debe superar los $500,000 (111.1 unidades).

📥 2. Carga y preparación de datos
Tareas:

Cargar los archivos geo_data_0.csv, geo_data_1.csv, geo_data_2.csv.

Verificar tipos de datos, valores nulos y estadísticas básicas.

Separar características (features) y variable objetivo (target).

Herramientas: pandas, numpy, matplotlib, seaborn.

🤖 3. Entrenamiento y validación del modelo
Para cada archivo:

División de datos: 75% entrenamiento, 25% validación (sin mezcla).

Modelo: Regresión lineal (LinearRegression de scikit-learn).

Evaluación:

Calcular el RMSE.

Calcular el volumen medio predicho.

Almacenar predicciones y valores reales para análisis posterior.

Funciones sugeridas:

train_and_validate_model(dataframe)

evaluate_model(y_true, y_pred)

💰 4. Preparación para el cálculo de ganancias
Tareas:

Calcular el volumen medio real de reservas por región.

Comparar con el umbral de 111.1 unidades.

Almacenar predicciones completas y top 200 por región.

Variables clave:

predictions_region_0, top_200_region_0, etc.

mean_volume_region_0, profit_region_0, etc.

📈 5. Cálculo de ganancias
Función: calculate_profit(predictions, actuals)

Lógica:

Seleccionar las 200 predicciones más altas.

Calcular el volumen real correspondiente.

Ganancia = volumen_real_total × $4,500 – $100,000,000

Conclusión: Comparar ganancias entre regiones y proponer la más rentable.

📊 6. Análisis de riesgo con bootstrapping
Función: bootstrap_profit(predictions, actuals, n_iterations=1000)

Tareas:

Tomar 1000 muestras aleatorias de 200 pozos.

Calcular la distribución de ganancias.

Obtener:

Beneficio promedio

Intervalo de confianza del 95%

Riesgo de pérdida (proporción de ganancias < 0)

Conclusión: Seleccionar la región con mayor beneficio promedio y riesgo < 2.5%.
