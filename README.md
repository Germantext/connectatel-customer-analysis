# Análisis de Comportamiento de Clientes — ConnectaTel

## Objetivo del proyecto

ConnectaTel es una empresa de telecomunicaciones con operaciones en México y Colombia. Este proyecto analiza cómo sus clientes usan realmente los servicios móviles (llamadas y mensajes), con el fin de identificar patrones de consumo, detectar comportamientos atípicos y construir segmentos de clientes accionables que ayuden a optimizar la oferta comercial y las estrategias de retención.

Preguntas de negocio que guían el análisis:

- ¿Qué segmentos de clientes muestran mayor o menor uso de llamadas y mensajes?
- ¿Qué usuarios presentan valores atípicos que puedan indicar comportamientos inusuales o errores de registro?
- ¿Cómo varía el uso según la edad y el tipo de plan contratado?
- ¿Qué segmentos representan mayor riesgo de cancelación (churn) y por qué?
- ¿Qué patrones pueden ayudar a diseñar mejores planes y mejorar la retención de clientes?

## Datasets utilizados

- **plans.csv**: catálogo de planes (precio, minutos incluidos, GB incluidos, costo por extra).
- **users_latam.csv**: información de cada cliente (edad, ciudad, fecha de registro, plan, fecha de cancelación).
- **usage.csv**: detalle de uso real — llamadas (duración) y mensajes (longitud).

## Etapas del análisis

1. **Carga y exploración inicial**: revisión de estructura, tipos de datos y dimensiones de los tres datasets.
2. **Identificación de problemas de calidad**: detección de nulos, valores centinela (sentinels) y fechas fuera de rango.
3. **Limpieza de datos**: corrección de sentinels, estandarización de fechas y tratamiento de valores nulos según su naturaleza (aleatorios vs. estructurales).
4. **Construcción de perfil de usuario**: agregación de la actividad de `usage` por cliente (mensajes, llamadas, minutos totales) y combinación con `users`.
5. **Estadística descriptiva y visualización de distribuciones**: análisis de edad, mensajes, llamadas y minutos de llamada, comparando por tipo de plan.
6. **Detección de outliers**: identificación de valores atípicos mediante el método IQR y decisión justificada sobre cuáles conservar.
7. **Segmentación de clientes**: por nivel de uso (bajo, medio, alto) y por grupo de edad (joven, adulto, adulto mayor), incluyendo cruce con tasa de cancelación (churn).
8. **Insight ejecutivo**: conclusiones y recomendaciones comerciales orientadas a retención y diseño de planes.

## Cómo ejecutar el notebook

1. Abre el archivo `.ipynb` en [Google Colab](https://colab.research.google.com/) o Jupyter Notebook.
2. Asegúrate de tener instaladas las librerías: `pandas`, `numpy`, `seaborn`, `matplotlib`.
3. Coloca los archivos `plans.csv`, `users_latam.csv` y `usage.csv` en la ruta `/datasets/` (o ajusta las rutas de carga según donde los tengas).
4. Ejecuta las celdas en orden, de arriba hacia abajo (`Kernel → Restart & Run All` para correr todo desde cero).

## Principales hallazgos

- El 14% de los registros de ciudad estaban vacíos o mal capturados, y se detectaron sentinels en edad (-999) y fechas de registro imposibles (año 2026).
- El comportamiento de mensajes y llamadas es muy similar entre los planes Básico y Premium, lo que sugiere una oportunidad de rediseñar la oferta de planes.
- El segmento de "Alto uso" (7% de la base) es el más rentable pero también el que presenta mayor tasa de cancelación (14% vs. 11.65% general), representando el mayor riesgo de pérdida de ingresos.
- Existe un nicho de clientes con consumo de minutos muy superior al resto (hasta 155 minutos frente a un uso típico de ~20), que podría beneficiarse de una oferta específica.

## Autor

Proyecto desarrollado como parte del Sprint 7 del bootcamp de Data Analyst (TripleTen).
