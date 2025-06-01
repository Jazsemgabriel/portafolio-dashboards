# 📈 Dashboard de Recursos Humanos | Visión 2024

Este proyecto de Power BI ofrece un análisis detallado de los principales indicadores de recursos humanos de una empresa para el año 2024. Permite evaluar la demografía de los empleados, la distribución por país y departamento, el rango salarial, la inclusión étnica y la retención.

---

## 🎯 Objetivo del Dashboard

Visualizar métricas clave para la gestión estratégica de talento y la toma de decisiones en el área de Recursos Humanos:

- **Análisis Demográfico:** Distribución de empleados por edad, país, departamento y etnia.
- **Eficiencia Operativa:** Salario promedio, horas trabajadas y duración promedio de empleo.
- **Diversidad e Inclusión:** Porcentaje de inclusión étnica y empleados con discapacidad.
- **Retención de Talento:** Tasa de retención anual y análisis de contrataciones.
- **Análisis Temporal:** Monitoreo de métricas clave a lo largo del año.

---

## 🧪 Proceso de desarrollo

Este dashboard fue construido a partir de un enfoque completo que incluyó:

### 1. Diseño y Planificación
Se planteó una interfaz visual clara y jerarquizada, orientada a ofrecer una visión integral y comparativa de los datos de RRHH.

### 2. Estructuración de la fuente de datos
La información original fue transformada y organizada en un **modelo dimensional en estrella**, separando las dimensiones (empleados, departamentos, ubicación, fecha) de la tabla de hechos, para asegurar la eficiencia del análisis.

### 3. Preparación y limpieza de datos
- Uso de **Power Query** para la transformación, limpieza y estandarización de los datos.
- Manejo de valores nulos, formatos de fecha uniformes y tipologías consistentes.
- Generación de claves y separación semántica de las entidades de RRHH.

### 4. Modelado relacional en Power BI
Se establecieron relaciones eficientes entre las tablas del modelo dimensional, priorizando la claridad y el rendimiento para facilitar la creación de medidas y visualizaciones precisas.

### 5. Creación de medidas con DAX
- Se desarrollaron métricas clave para el análisis de personal, incluyendo totales de empleados, salarios, promedios y porcentajes de variación.
- Se implementaron medidas para el cálculo de indicadores de diversidad y retención.

---

## 🧱 Modelo Dimensional

Este dashboard está basado en un modelo estrella con las siguientes tablas:

**Tabla de hechos:**
- `fct_hechos`: contiene datos como costo/beneficio de la empresa, evaluación de desempeño, grupo salarial, horas trabajadas, eventos y fechas.

**Dimensiones:**
- `dim_departamentos`
- `dim_ubicacion`
- `dim_empleados`
- `dim_fecha`

📌 *Modelo relacional ilustrado:*
![Modelo Relacional](./modelado.png)

---

## 📊 Vistas del Dashboard

El dashboard presenta una vista principal para el análisis del año actual:

### 1. Overview 2024
Esta página muestra un resumen de los indicadores de recursos humanos para el año 2024, incluyendo el total de empleados, contratados, salario anual promedio, edad promedio, distribución por país, departamento, rango etario, empleados con discapacidad y porcentaje de inclusión étnica y retención.

![Página Overview 2024](./02.overview_2024.png)

---

## 🧠 Medidas DAX

Entre las medidas DAX utilizadas para los cálculos del dashboard, destacan:

- `baseline`
- `bg_color_contratados`
- `bg_color_edad`
- `bg_color_empleados`
- `bg_color_etnia`
- `bg_color_retencion`
- `bg_variacion_salario`
- `color_icono_contratados`
- `color_icono_edad`
- `color_icono_empleados`
- `color_icono_etnia`
- `color_icono_retencion`
- `color_icono_salario`
- `costo_total_salario`
- `diff_contratados`
- `diff_edad`
- `diff_empleados`
- `diff_etnia`
- `diff_retencion`
- `diff_salario`
- `empleado_fuera`
- `indice_retencion`
- `indice_retencion_anio_anterior`
- `media_salarial_anual`
- `media_salarial_anual_anio_anterior`
- `porcentaje_inclusion_etnica`
- `porcentaje_inclusion_etnica_anio_anter...`
- `promedio_duracion_empleados`
- `promedio_duracion_empleados_anio_ant...`
- `promedio_edad`
- `promedio_edad_anio_anterior`

📌 *Captura de medidas en Power BI:*
![Medidas](./medidas.png)

---

## 🧩 Conclusiones

Basado en las visualizaciones del dashboard, se pueden extraer las siguientes conclusiones:

- El número total de empleados se ha mantenido estable en 2024.
- El salario anual promedio muestra un ligero incremento en 2024.
- Perú, Uruguay y Chile son los países con mayor concentración de empleados en 2024.
- Finanzas y Marketing son los departamentos con más empleados.
- La distribución por rango etario muestra que la mayoría de los empleados se encuentran entre los 25 y 40 años.
- La inclusión étnica y la retención anual son métricas importantes que deben ser monitoreadas.

---

## 🛠️ Herramientas utilizadas

- Power BI Desktop
- Power Query
- DAX

---

## 👤 Autor

Gabriel Rodríguez
[LinkedIn](https://www.linkedin.com/in/gabriel-rodr%C3%ADguez-4b4a6216b/)

---
