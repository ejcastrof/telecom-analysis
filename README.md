# Análisis de uso de clientes – ConnectaTel

Proyecto del Sprint 7 (TripleTen, Data Analyst): análisis estadístico para detectar patrones de uso y valores atípicos en los clientes de ConnectaTel, empresa de telecomunicaciones con operaciones en México y Colombia. Los datos cubren el año 2024.

## Objetivo

Entender cómo usan los clientes las llamadas y los mensajes, detectar comportamientos atípicos y construir segmentos por edad y nivel de uso que sirvan para mejorar la oferta de planes.

## Datasets

| Archivo | Contenido |
|---|---|
| `plans.csv` | Catálogo de planes (precio, minutos y GB incluidos, costo por extra). 2 filas. |
| `users_latam.csv` | Clientes: edad, ciudad, fecha de registro, plan y fecha de baja. 4,000 filas. |
| `usage.csv` | Uso real: llamadas (duración) y mensajes (longitud). 40,000 filas. |

## Etapas del análisis

1. **Carga y exploración:** estructura, tipos de datos y tamaño de cada dataset.
2. **Calidad de datos:** conteo de nulos, detección de valores centinela (-999 en `age`, "?" en `city`) y de fechas imposibles (años 2026).
3. **Limpieza:** reemplazo de centinelas por la mediana o por nulo, y marcado de fechas futuras como nulas. Los nulos de `duration` y `length` se conservaron porque dependen del tipo de evento (llamada o mensaje).
4. **Estadísticas por usuario:** métricas de cantidad de mensajes, cantidad de llamadas y minutos de llamada, combinadas con la tabla de usuarios.
5. **Visualización y outliers:** histogramas por plan, boxplots y detección con el método IQR.
6. **Segmentación:** grupos por nivel de uso (Bajo, Medio, Alto) y por edad (Joven, Adulto, Adulto Mayor).
7. **Insight ejecutivo:** conclusiones y recomendaciones de negocio.

## Hallazgos principales

- El 73.6% de los clientes tiene uso medio, el 19.5% bajo uso y el 7.0% alto uso.
- El uso es casi idéntico entre los planes Básico y Premium, y cambia poco según la edad.
- Hay 109 clientes con minutos de llamada atípicos (más de 61.9 minutos), y un grupo de más de 120 minutos que conviene revisar.
- 14.1% de los clientes no tiene ciudad conocida, un límite para segmentar por ubicación.

## Cómo ejecutar el notebook

1. Abre el notebook en Google Colab o Jupyter Notebook.
2. Coloca los tres archivos CSV en una carpeta accesible y ajusta las rutas de lectura (`/datasets/...`) a su ubicación.
3. Ejecuta todas las celdas en orden (**Runtime → Run all** en Colab, o **Kernel → Restart & Run All** en Jupyter).

**Requisitos:** Python 3 con `pandas`, `numpy`, `matplotlib` y `seaborn`.

## Autor

Elkin Javier Castro Fonseca
LinkedIn: www.linkedin.com/in/elkin-castro-fonseca

