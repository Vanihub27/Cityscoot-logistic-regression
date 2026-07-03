# 🛴 CityScoot – Predicción de Demanda mediante Regresión Logística

> Cómo elegir el modelo adecuado según el objetivo de negocio.

---

# 📌 Descripción del proyecto

CityScoot, una empresa de micromovilidad urbana, busca anticipar la demanda diaria de scooters para optimizar la asignación de flota, la estrategia de precios y la planificación operativa.

Inicialmente el problema se abordó como una tarea de **regresión**, con el objetivo de predecir el número exacto de viajes diarios. Sin embargo, el requerimiento de negocio evolucionó hacia un problema de **clasificación binaria**: identificar si un día presentará **alta** o **baja demanda**.

Este proyecto muestra cómo la correcta elección del modelo depende del objetivo de negocio y justifica por qué la **Regresión Logística** resulta más adecuada que la Regresión Lineal para este caso.

---

# 🎯 Objetivo de negocio

Clasificar cada día como:

- 🔴 **Alta demanda:** más de 1200 viajes
- 🔵 **Baja demanda:** 1200 viajes o menos

El modelo estima la probabilidad de que un día pertenezca a la categoría **Alta Demanda**, permitiendo anticipar decisiones operativas.

---

# 📊 Dataset

El conjunto de datos contiene información diaria relacionada con la operación de CityScoot.

## Variables predictoras

- Temperatura (`temp_c`)
- Precipitación (`rain_mm`)
- Inversión en marketing (`marketing_spend`)
- Precio por minuto (`price_per_min`)
- Fin de semana (`is_weekend`)
- Feriado (`is_holiday`)
- Evento en la ciudad (`city_event`)

## Variable objetivo

- `high_demand`

---

# 🧠 Estrategia analítica

El proyecto compara dos enfoques de modelado para evidenciar la importancia de seleccionar el algoritmo adecuado.

## Regresión Lineal

Se entrenó inicialmente un modelo de Regresión Lineal tratando la variable objetivo como continua.

Esto permitió identificar sus principales limitaciones:

- Predicciones fuera del intervalo [0,1]
- Optimización mediante Error Cuadrático Medio (MSE)
- Probabilidades no válidas
- Escasa interpretación para problemas de clasificación

## Regresión Logística

Posteriormente se implementó un modelo de Regresión Logística, adecuado para clasificación binaria.

Sus principales ventajas fueron:

- Probabilidades calibradas
- Optimización mediante Log-Loss
- Interpretación mediante Odds Ratio
- Mejor alineación con el objetivo de negocio

---

# ⚙️ Pipeline de modelado

- Selección de variables
- División Train/Test (75/25)
- Muestreo estratificado
- Escalado con StandardScaler
- Entrenamiento del modelo
- Evaluación de desempeño
- Interpretación de coeficientes

---

# 📈 Métricas evaluadas

- Accuracy
- Precision
- Recall
- ROC-AUC
- Log-Loss
- Matriz de confusión

---

# 💡 Principales resultados

El modelo de Regresión Logística obtuvo probabilidades consistentes y una adecuada capacidad discriminativa entre días de alta y baja demanda.

La evaluación permitió analizar distintos compromisos entre precisión y sensibilidad para apoyar decisiones operativas.

---

# 📊 Interpretación del modelo

Los coeficientes fueron transformados a **Odds Ratios** para facilitar su interpretación.

Esto permitió cuantificar el impacto de variables como:

- inversión en marketing
- lluvia
- fines de semana
- eventos urbanos

sobre la probabilidad de registrar una jornada de alta demanda.

---

# 🚲 Impacto para el negocio

El modelo permite:

- anticipar días críticos
- optimizar la asignación de scooters
- ajustar estrategias de precios
- optimizar campañas de marketing
- reducir riesgos asociados a picos de demanda

---

# ⭐ Aprendizajes

Más allá del desempeño predictivo, el principal aporte del proyecto fue demostrar la importancia de seleccionar el modelo estadístico adecuado según el problema de negocio.

El trabajo evidencia:

- comprensión conceptual de modelos supervisados
- pensamiento estadístico
- interpretación probabilística
- traducción de resultados técnicos en decisiones de negocio

---

# 🛠️ Tecnologías utilizadas

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib

---

# 💼 Competencias demostradas

- Clasificación binaria
- Regresión Logística
- Modelado probabilístico
- Interpretación mediante Odds Ratio
- Evaluación de modelos
- Machine Learning aplicado
- Storytelling con datos
- Business Analytics

---

## 👩‍💻 Autora

**Vanina Cavallin**

Doctora en Ciencias Biológicas | Jr. Data Scientist
