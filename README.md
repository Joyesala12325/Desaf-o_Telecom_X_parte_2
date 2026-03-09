# Desaf-o_Telecom_X_parte_2
El Desafío Telecom X parte 2 ofrece una oportunidad única para aplicar conocimientos fundamentales de estadística, regresión lineal y machine learning, además de habilidades esenciales en ciencia de datos, en un escenario empresarial real.

# 🤖 Telecom X - Parte 2: Modelado Predictivo de Cancelación (Churn)

## 📝 Descripción del Proyecto
Tras concluir la fase de Análisis Exploratorio (EDA), este proyecto avanza hacia la implementación de inteligencia predictiva. El objetivo de esta segunda fase es desarrollar, evaluar e interpretar modelos de Machine Learning capaces de identificar con anticipación qué clientes tienen un alto riesgo de cancelar su servicio. Esto permite a Telecom X pasar de una postura reactiva a una estrategia de retención proactiva.

## 🎯 Objetivos
* **Preprocesamiento Avanzado:** Preparar un dataset estructurado para el modelado matemático.
* **Ingeniería y Selección de Variables:** Analizar correlaciones y descartar características redundantes.
* **Entrenamiento de Modelos:** Implementar algoritmos de clasificación supervisada.
* **Evaluación Crítica:** Medir el rendimiento utilizando métricas de negocio (priorizando el *Recall*).
* **Interpretabilidad (Data Storytelling):** Extraer la importancia de las variables para generar estrategias de retención.

## 🛠️ Tecnologías y Librerías
* **Lenguaje:** Python 3
* **Manipulación de Datos:** Pandas, NumPy
* **Machine Learning:** Scikit-Learn (`LogisticRegression`, `RandomForestClassifier`)
* **Balanceo de Datos:** Imbalanced-learn (`SMOTE`)
* **Visualización:** Matplotlib, Seaborn

## 🚀 Arquitectura del Pipeline de Machine Learning

### 1. Preparación de los Datos (Preprocesamiento)
* **Limpieza:** Eliminación de variables identificadoras sin valor predictivo (`customerID`).
* **Codificación (Encoding):** Transformación de variables categóricas a formato numérico utilizando *One-Hot Encoding* (`pd.get_dummies`), evitando la multicolinealidad.
* **Balanceo de Clases:** Aplicación de **SMOTE** (Synthetic Minority Over-sampling Technique) para corregir el desbalance original (73% retención vs 26% cancelación) y evitar sesgos en el algoritmo.
* **Escalado:** Uso de `StandardScaler` para normalizar las variables continuas, garantizando el correcto funcionamiento de modelos sensibles a la distancia y magnitud.

### 2. Correlación y Selección de Variables
* Creación de **Mapas de Calor (Heatmaps)** para evaluar la colinealidad entre características numéricas.
* Visualización con **Boxplots** para confirmar de manera aislada la relación inversa entre el tiempo de contrato (*Tenure*) y la probabilidad de evasión.

### 3. Modelado Predictivo
Se entrenaron y compararon dos arquitecturas de clasificación:
1. **Regresión Logística:** Modelo lineal e interpretable, entrenado con datos estandarizados.
2. **Random Forest (Bosque Aleatorio):** Modelo de ensamble basado en árboles de decisión, entrenado con datos sin escalar por su naturaleza robusta ante magnitudes.

### 4. Evaluación de Rendimiento
Se priorizó la métrica de **Sensibilidad (Recall)**, ya que el costo de oportunidad de perder un cliente (Falso Negativo) es significativamente mayor que el de ofrecer una promoción a un cliente que se iba a quedar (Falso Positivo).
* **Random Forest** demostró un desempeño superior, logrando clasificar correctamente a la inmensa mayoría de los clientes en riesgo de fuga, minimizando drásticamente los falsos negativos en la Matriz de Confusión.

## 💡 Importancia de Variables e Insights
Al analizar la reducción de impureza en Random Forest y los coeficientes de la Regresión Logística, se identificaron los detonantes del Churn:
1. **El Contrato Mensual es Crítico:** La variable de contrato *Month-to-month* es el principal factor de riesgo predictivo.
2. **Ciclo de Vida Temprano:** A menor tiempo de antigüedad (*Tenure*), la probabilidad de abandono se dispara.
3. **Sensibilidad al Valor:** Variables relacionadas con la facturación y el uso de cheques electrónicos mostraron un impacto negativo en la retención.

## 📈 Recomendaciones Estratégicas
* **Incentivar la migración de contratos:** Diseñar campañas para trasladar a los clientes mensuales hacia contratos anuales mediante mejoras de servicio.
* **Fidelización Temprana:** Concentrar los esfuerzos de retención y soporte técnico durante los primeros 6 meses de vida del cliente.
