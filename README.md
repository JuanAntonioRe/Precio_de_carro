# Precio de tu carro :rocket:
Para este proyecto se hace uso de algoritmos de descenso de gradiente y potenciación del gradiente

El gradiente indica la dirección en la que la función crece más rápido. Sin embargo, no sirve para resolver el problema de minimización. Necesitamos el gradiente negativo, que es un vector opuesto que muestra el decrecimiento más rápido.

El descenso de gradiente es un algoritmo iterativo para encontrar el mínimo de la función de pérdida. Sigue la dirección del gradiente negativo y se aproxima gradualmente al mínimo. Y la potenciación es el descenso de gradientes funcionales iterativos.

## Descripción del proyecto
Rusty Bargain es un servicio de venta de coches de segunda mano que está desarrollando una app para atraer a nuevos clientes. Gracias a esa app, se puede averiguar rápidamente el valor de mercado de tu coche.

El dataset tiene información de especificaciones técnicas, versiones de equipamiento, precios, entre otros datos.

## Objetivo
Crear un modelo que determine el valor de mercado de un carro.

A Rusty Bargain le interesa:
* La calidad de la predicción
* La velocidad de la predicción
* El tiempo requerido para el entrenamiento


## Desarrollo del proyecto
### Descarga y preparación de los datos.
Se importaron los datos utilizando Pandas revisando si hay valores ausentes o duplicados y se explica como se procesaron. Además se explica la eliminación de columnas que no contienen información útil para el modelo.

También se realiza una codificación OHE ya que para algunos modelos que se entrenan es necesario hacer esta codificación.

### Entrenamiento de los modelos.
Se separan las características del objetivo y a su vez en el conjunto de entrenamiento y validación.

Se entrena un modelo de regresión linear con el objetivo de que sirva como prueba de cordura, ya que la regresión lineal no es muy buena para el ajuste de hiperparámetros. Si la potenciación del gradiente funciona peor que la regresión lineal, definitivamente algo salió mal.

Los modelos de potenciación de gradiente que se entrenan son:
* CatBoost
* LightGBM
* XGBoost

De estos modelos XGBoost es el que necesita una codificación OHE en los datos. Para los tres modelos se toma el tiempo de ejecución usando un magic command: `%%time`. Además a todos se les ha tomado el valor de RMSE. El valor con mejor tiempo y RMSE es el seleccionado.

## Conclusiones
Los modelos que usan potenciación del gradiente dan mejor resultado, en cuanto al RMSE, al manejar diferentes hiperparámetros.

**LightGBM** dio el mejor resultado de RMSE y el menor tiempo de ejecución. Por lo que es el mejor modelo para realizar la tarea de predicción del precio de autos.

## Tecnologías
* Pandas
* sklearn:
    + preprocessing.StandardScaler
    + model_selection.train_test_split
    + metrics.mean_squared_error
    + linear_model.LinearRegression
    + ensemble.RandomForestRegressor
* catboost.CatBoostRegressor
* lightgbm.LGBMRegressor
* xgboost.XGBRegressor