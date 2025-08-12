# TelecomX_parte2_entrega.ipynb
En este repositorio se encuentra el Challenge Telecom X: análisis de evasión de clientes - Parte 2




#----------------

# TELECOM X - PREDICCIÓN DE CANCELACIÓN (Churn)

## 📊 Introducción

Este proyecto se enfoca en el análisis y predicción de la cancelación de clientes (churn) en una empresa de telecomunicaciones. Utilizando datos históricos, se busca identificar los factores clave que influyen en la decisión de un cliente de cancelar su servicio y desarrollar modelos predictivos para anticipar este comportamiento.

## 📌 Extracción y Preparación de Datos

Los datos fueron cargados desde un archivo CSV (`df_limpo.csv`). Se realizó un preprocesamiento exhaustivo que incluyó:

- Eliminación de columnas irrelevantes (`customerID`).
- Agrupación de categorías en variables categóricas (ej: "No internet service" como "No").
- Aplicación de One-Hot Encoding para convertir variables categóricas en numéricas.
- Manejo de valores nulos en las columnas `Total.Day` y `account.Charges.Total` mediante la eliminación de las filas correspondientes.

## 🛠️ Análisis Exploratorio de Datos y Multicolinealidad

Se realizó un análisis de correlación para entender las relaciones entre las variables y la variable objetivo (`Churn_Yes`). Se visualizó un heatmap de correlación, filtrando por variables con una correlación absoluta mayor o igual a 0.2 con la variable objetivo.

Se llevó a cabo un análisis de Factor de Inflación de la Varianza (VIF) para detectar y tratar la multicolinealidad entre las variables predictoras. Se identificaron y eliminaron variables con alta o perfecta multicolinealidad para asegurar la estabilidad de los modelos lineales.

## 🤖 Modelos Predictivos

Se entrenaron dos modelos de clasificación para predecir el churn:

- **Regresión Logística**
- **Random Forest**

Para abordar el desbalance de clases en la variable objetivo, se utilizó la técnica SMOTE en el conjunto de entrenamiento. Los datos numéricos fueron normalizados utilizando `StandardScaler` antes del entrenamiento.

### Rendimiento de los Modelos

| Modelo             | Exactitud | ROC AUC | Precision (Churn=Yes) | Recall (Churn=Yes) | F1-Score (Churn=Yes) |
|--------------------|-----------|---------|-----------------------|--------------------|----------------------|
| Regresión Logística | 0.7502    | 0.8454  | 0.52                  | 0.81               | 0.63                 |
| Random Forest      | 0.7787    | 0.8242  | 0.58                  | 0.60               | 0.59                 |

Ambos modelos demuestran una buena capacidad predictiva, con ROC AUC superior a 0.8. La Regresión Logística muestra un mejor recall para la clase positiva (churn), lo cual es importante para identificar a los clientes en riesgo.

## 🔍 Identificación de Factores Clave de Churn

El análisis de los modelos reveló que los factores más influyentes en la cancelación son:

- **Antigüedad del Cliente (`customer.tenure`):** Menor antigüedad se asocia con mayor probabilidad de churn.
- **Cargos (`account.Charges.Monthly`, `account.Charges.Total`):** Cargos más altos incrementan el riesgo de churn.
- **Servicio de Internet (`internet.InternetService_Fiber optic`, `internet.InternetService_No`):** Clientes con fibra óptica tienen mayor probabilidad de churn, mientras que aquellos sin internet tienen menor probabilidad.
- **Tipo de Contrato (`account.Contract_Two year`, `account.Contract_One year`):** Contratos a largo plazo reducen el churn.
- **Método de Pago (`account.PaymentMethod_Electronic check`):** El pago con cheque electrónico se asocia con mayor churn.
- **Servicios Adicionales:** La falta de servicios como soporte técnico, seguridad en línea, copia de seguridad y protección de dispositivos aumenta el riesgo de churn.

## 💡 Estrategias de Retención Propuestas

Basado en los hallazgos, se proponen las siguientes estrategias para reducir la cancelación:

- Implementar programas de fidelización para clientes nuevos y de baja antigüedad.
- Optimizar los planes de servicio y la comunicación de valor para clientes con altos cargos.
- Investigar y mejorar la experiencia de los clientes con servicio de fibra óptica.
- Incentivar la adopción de contratos a largo plazo.
- Analizar y optimizar el proceso de pago con cheque electrónico, fomentando métodos de pago más estables.
- Promover y educar sobre los beneficios de los servicios de valor agregado.

## ⏭️ Próximos Pasos

- Optimización de hiperparámetros y validación cruzada para mejorar el rendimiento del modelo.
- Análisis más profundo de los factores influyentes específicos.
- Segmentación de clientes por riesgo para aplicar estrategias de retención personalizadas.
- Implementación y seguimiento de las estrategias de retención propuestas.
- Exploración de otros modelos de clasificación.
