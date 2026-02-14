---
# 🚲 CityScoot – Clasificación Binaria de Demanda
## De Regresión Lineal a Regresión Logística (Framework de Decisión de Modelado)
---

### Resumen Ejecutivo

#### CityScoot, empresa de micromovilidad urbana, busca anticipar el nivel de demanda diaria para optimizar la asignación de flota, la estrategia de precios y la planificación operativa.

→ El enfoque analítico inicial consistía en predecir el número exacto de viajes diarios mediante regresión lineal. Sin embargo, el objetivo de negocio evolucionó: En lugar de predecir un valor exacto, el objetivo pasó a ser clasificar los días en Alta Demanda o Baja Demanda.
→ Este proyecto demuestra la transición metodológica de un problema de regresión a uno de clasificación, justificando por qué la regresión logística es estadística y conceptualmente el modelo adecuado para la toma de decisiones binarias.

#### Objetivo de Negocio: Clasificar cada día como 🔴Alta Demanda → Más de 1200 viajes / 🔵Baja Demanda → 1200 viajes o menos
#### El modelo debe estimar la probabilidad de que un día pertenezca a la categoría “Alta Demanda”.


## Descripción del Dataset

### Datos operativos diarios que incluyen:
- Temperatura (temp_c)
- Lluvia (rain_mm)
- Inversión en marketing (marketing_spend)
- Precio por minuto (price_per_min)
- Indicador de fin de semana (is_weekend)
- Indicador de feriado (is_holiday)
- Evento en la ciudad (city_event)
- **Variable objetivo binaria: high_demand**

🧠 Estrategia Analítica

Aunque el enfoque inicial utilizaba regresión lineal, la variable objetivo es binaria. 
Por lo tanto:
- La regresión lineal optimiza MSE.
- Los problemas de clasificación requieren modelado probabilístico.
- La regresión logística optimiza log-loss.

→ Este proyecto compara intencionalmente ambos enfoques para evidenciar la importancia de seleccionar el modelo correcto según el objetivo del negocio.

→ Pipeline de Modelado
Selección de variables relevantes:
- División train-test (75/25)
- Muestreo estratificado para mantener proporción de clases
- Escalado de variables mediante StandardScaler

→ Primer modelo que se intentó = Regresión Lineal (Modelo Incorrecto para Clasificación).
Se entrena una regresión lineal tratando el target binario como continuo y se detectan los siguientes problemas:
- Predicciones fuera del rango [0,1]
- Optimización de MSE (no apropiada para clasificación)
- Interpretación probabilística inválida
- Aunque puede arrojar un accuracy aparentemente aceptable con un umbral forzado, el modelo carece de coherencia estadística para clasificación.

→ Modelo Correcto = Regresión Logística
- Produce probabilidades válidas
- Optimiza log-loss
- Permite interpretación mediante odds ratio
- Es conceptualmente adecuada para decisiones binarias

→ Se evaluaron las siguientes métricas: 
- Log-loss → Calidad de las probabilidades estimadas
- Accuracy → Proporción de clasificaciones correctas
- Precision → Fiabilidad al predecir alta demanda
- Recall → Capacidad de detectar días de alta demanda
- ROC-AUC → Poder discriminativo global del modelo
- Matriz de confusión → Estructura de errores

→ Insights de Performance:
- La regresión logística entrega probabilidades calibradas y coherentes.
- El ROC-AUC muestra buena capacidad de separación entre clases.
- El log-loss confirma calidad en la estimación probabilística.
- Precision y recall permiten evaluar trade-offs operativos.

→ Esto habilita decisiones estratégicas como:
- Reasignación anticipada de scooters
- Ajuste dinámico de precios
- Optimización del gasto en marketing

→ Interpretación de Coeficientes (Enfoque de Negocio)
→ Los coeficientes del modelo logístico se transformaron en odds ratio:

- 𝑂𝑑𝑑𝑠 𝑅𝑎𝑡𝑖𝑜= 𝑒𝛽 
- Odds Ratio=eβ

→ Esto permite interpretar: 
- Cuánto aumenta la probabilidad de alta demanda ante mayor inversión en marketing.
- Cómo impacta la lluvia en la probabilidad de alta demanda.
- Qué efecto tienen fines de semana o eventos urbanos.
- Este paso conecta el modelo estadístico con la toma de decisiones estratégicas.

→ Impacto en Negocio - El modelo final permite:
- Clasificación anticipada de días críticos
- Optimización de recursos operativos
- Mitigación de riesgos en picos de demanda
- Toma de decisiones basada en probabilidad, no solo en estimaciones puntuales
- La transición de regresión a clasificación alinea la técnica analítica con la necesidad real del negocio.

**Aprendizaje Clave: El principal valor de este proyecto no es únicamente el rendimiento del modelo, sino la correcta selección metodológica.**

→ Demuestra:
- Rigor conceptual
- Comprensión estadística
- Capacidad de traducir objetivos de negocio en decisiones técnicas
- Madurez analítica

→ Tecnologías Utilizadas
- Python
- NumPy
- Pandas
- Matplotlib
- Scikit-learn


---
Vanina Cavallin.
Autora: Dra. en Cs. Biológicas.
Jr. Data Scientist.
---