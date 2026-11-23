# IA para predicción ambiental en centros de cultivo acuícola

> **English summary.** MSc in Artificial Intelligence thesis (UNIR). Deep learning on the outputs of the CROCO-OCEAN high-resolution ocean model to predict time series of environmental variables at a real salmon-farming concession in southern Chile. Includes the NetCDF-to-time-series data engineering and a systematic comparison of DNN, CNN and RNN models. The rest of this document is in Spanish.

**Prototipo experimental de IA para modelos biogeoquímicos e hidrodinámicos oceanográficos en centros de cultivo, para la predicción de variables e impacto ambiental.**

Trabajo Fin de Máster — Máster Universitario en Inteligencia Artificial (UNIR) · Giocrisrai Godoy Bonillo

[![Python](https://img.shields.io/badge/Python-3670A0?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)
[![Domain](https://img.shields.io/badge/dominio-acuicultura%20%2F%20oceanograf%C3%ADa-0a6a79?style=flat-square)](#)

> **Por qué este trabajo importa hoy.** La salmonicultura chilena está obligada a entregar Información Ambiental (INFA) periódica a Sernapesca sobre la condición de la columna de agua y el sedimento de cada concesión. Este prototipo aborda exactamente ese problema: **predecir, a partir de un modelo oceanográfico, las variables ambientales que determinan el riesgo de un centro de cultivo** — antes de que ocurra el evento adverso. Es la base metodológica de una línea de monitoreo ambiental predictivo para acuicultura en aguas reguladas.

---

## Problema

Un centro de cultivo de salmones opera bajo condiciones oceanográficas que cambian en el tiempo (temperatura, salinidad, corrientes, oxígeno, variables biogeoquímicas). Cuando esas variables cruzan ciertos umbrales, se generan **impactos ambientales** y **riesgos operacionales** (mortalidad, prealerta, pérdida de la resolución de calificación ambiental). Anticiparlas con horas o días de ventaja tiene valor económico y regulatorio directo.

Este trabajo desarrolla la **interacción entre algoritmos de aprendizaje profundo y un modelo oceanográfico de alta resolución** para predecir las series temporales de esas variables en una concesión marítima real.

## Zona de estudio y datos

- **Sitio:** una concesión marítima en el extremo sur de Chile (**Islas Clarence**, región de Magallanes), con estudio de línea base oceanográfico real.
- **Fuente:** salidas del modelo oceanográfico **CROCO-OCEAN** (Coastal and Regional Ocean COmmunity model) en formato **NetCDF**, para campañas de **verano** e **invierno**, más **batimetría** del sector y la **posición de la jaula** del centro de cultivo.
- **Ingeniería de datos:** transformación de las salidas NetCDF (mallas espacio-temporales por capas de profundidad) a **series temporales en CSV** ancladas al punto de la concesión, para su manipulación y modelado.

## Enfoque

Comparación sistemática de tres familias de redes neuronales sobre el problema de predicción de series temporales:

| Arquitectura | Rol en el estudio |
|---|---|
| **DNN** (densa) | Línea base sin estructura temporal explícita |
| **CNN** (convolucional) | Captura de patrones locales en la ventana temporal |
| **RNN** (recurrente) | Modelado de dependencia temporal secuencial |

El objetivo es **determinar qué familia obtiene mejores métricas** para monitorear y predecir las variables que afectan al centro de cultivo. Los resultados completos, la metodología y las métricas comparadas están en la memoria depositada.

## Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `Transformacion_data_croco_tfm.ipynb` | Ingeniería de datos: lectura de NetCDF (CROCO-OCEAN), extracción por capas y construcción de la serie temporal en CSV. |
| `analisis_de_datos_proyecto_croco_inteligencia_artificial.ipynb` | Exploración de datos, batimetría, máscara del dominio y modelado comparativo (DNN/CNN/RNN). |
| `Datos_serie_temporal_TFM.ipynb` | Serie temporal consolidada y experimentos. |
| `csv_croco_his3feb_mar/` | Series temporales derivadas (CSV) de las campañas. |
| `TFM_Giocrisrai_Godoy_Bonillo_Deposito_extraordinaria.pdf` | Memoria completa del TFM (metodología, resultados, discusión). |

## Stack

`Python` · `TensorFlow / Keras` · `xarray / netCDF4` · `NumPy` · `Pandas` · `Matplotlib`

## De la investigación a la aplicación

Este prototipo es la semilla metodológica de un producto de **inteligencia ambiental para acuicultura**: ingesta de modelos oceanográficos y sensores, predicción de variables de riesgo, y prealerta temprana alineada con la reportería ambiental exigida por el regulador. El puente entre el modelo físico (CROCO-OCEAN), el dato del centro y el aprendizaje profundo es exactamente donde la IA agrega valor en este dominio.

## Cita

```
Godoy Bonillo, G. (2021). Prototipo experimental de IA para modelos biogeoquímicos
e hidrodinámicos oceanográficos en centros de cultivo para la predicción de variables
e impacto ambiental. Trabajo Fin de Máster, Máster Universitario en Inteligencia
Artificial, Universidad Internacional de La Rioja (UNIR).
```

## Licencia

Ver [`LICENSE`](LICENSE). Los datos oceanográficos derivados se incluyen con fines académicos y de reproducibilidad.

---

*Autor: **Giocrisrai Godoy Bonillo** — AI Engineer. Ingeniería de IA para industrias reguladas (acuicultura, medio ambiente marino, manufactura). [github.com/Giocrisrai](https://github.com/Giocrisrai) · [giocrisrai.com](https://giocrisrai.com)*
