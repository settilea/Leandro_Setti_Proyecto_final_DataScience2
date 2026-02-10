# 🚖 NYC Taxi Trip Duration Analysis & Prediction

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Colab](https://img.shields.io/badge/Platform-Google%20Colab-orange.svg)
![Status](https://img.shields.io/badge/Status-En%20Desarrollo-yellow.svg)

## 📋 Descripción del Proyecto
Este proyecto de Data Science tiene como objetivo predecir la duración total de viajes en taxi en la ciudad de Nueva York. Utilizando un enfoque de **Machine Learning** y **Análisis Geoespacial**, el modelo no solo considera variables temporales (hora/día), sino que enriquece los datos con información climática y características espaciales complejas (barrios y rutas teóricas).

El proyecto simula un escenario real de logística urbana donde la estimación precisa del tiempo de llegada (ETA) es crítica para la eficiencia operativa.

## 🎯 Objetivos
* Realizar un Análisis Exploratorio de Datos (EDA) profundo sobre el dataset de Taxis de NYC.
* Enriquecer el dataset original con datos externos: **Clima** y **Polígonos de Barrios (GeoJSON)**.
* Implementar ingeniería de características geoespaciales (Spatial Joins) para determinar zonas de origen y destino.
* Utilizar la **API de OSRM** para calcular rutas óptimas teóricas y comparar distancias de manejo vs. distancias euclidianas (se desestimó porque la API no deja aplicar la consulta de forma intensiva para todas las líneas del dataframe).
* Entrenar modelos de regresión (Linear, Random Forest, XGBoost) para predecir la duración del viaje.

## 💾 Fuente de Datos
1.  **Principal:** [NYC Taxi Trip Duration (Kaggle)](https://www.kaggle.com/datasets/yasserh/nyc-taxi-trip-duration) - Contiene timestamps y coordenadas.
2.  **Clima:** Datos históricos de clima en NYC para el periodo correspondiente (2016).
3.  **Geográficos:**
    * NYC Borough Boundaries (GeoJSON).
    * **OSRM API (Open Source Routing Machine):** Utilizada para simular la ruta de navegación real.

## 🛠️ Stack Tecnológico
El proyecto fue desarrollado íntegramente en **Google Colab**.

* **Procesamiento:** `Pandas`, `NumPy`
* **Geoespacial:** `GeoPandas`, `Shapely`, `Folium` (Mapas interactivos), `Polyline`.
* **APIs & Conectividad:** `Requests` (para consultar OSRM).
* **Machine Learning:** `Scikit-Learn` (Preprocesamiento, Modelado y Métricas).
* **Visualización:** `Matplotlib`, `Seaborn`.

## ⚙️ Metodología
1.  **Data Cleaning:** Limpieza de outliers (viajes de >3 horas, coordenadas fuera de la ciudad, velocidades imposibles).
2.  **Feature Engineering:**
    * Extracción de características temporales (Día semana, Hora pico, Festivos).
    * *Spatial Join:* Asignación de coordenadas GPS a Barrios (Manhattan, Queens, etc.).
    * *Weather Integration:* Cruce de datos de lluvia/nieve por hora.
3.  **Análisis de Rutas (OSRM):** Consulta a la API para obtener la distancia real de manejo y compararla con la distancia lineal.
4.  **Modelado:** Entrenamiento y validación de modelos predictivos.
