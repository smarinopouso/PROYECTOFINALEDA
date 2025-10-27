# Proyecto Final: Análisis Comparativo Ventas vs Presupuesto

## Descripción del Proyecto

Este proyecto realiza un análisis exploratorio de datos (EDA) comparativo entre las ventas reales y el presupuesto asignado para el año 2024. El objetivo es identificar patrones, desviaciones y oportunidades de mejora en el desempeño financiero y operativo.

## Estructura del Proyecto

```
PROYECTOFINALEDA/
├── data/
│   ├── raw/                    # Datos originales
│   │   ├── ventas2024.csv      # Datos de ventas bruto
│   │   └── presupuesto2024.xlsx # Datos de presupuesto bruto
│   ├── output/                 # Datos procesados
│   │   ├── ventas2024_limpio.csv
│   │   ├── presupuesto2024_limpio.xlsx
│   │   └── final/
│   │       └── df_final_completo.csv
├── notebook/                   # Notebooks de análisis
│   ├── 01-Analisis_ventas.ipynb
│   ├── 02-Analisis_presupuesto.ipynb
│   └── 03-Analisis_ventas_presupuesto.ipynb
└── README.md                   # Documentación del proyecto
```

## Notebooks de Análisis

### 1. 01-Analisis_ventas.ipynb
**Objetivo:** Análisis y limpieza del dataset de ventas

**Procesos realizados:**
- Carga y exploración inicial de datos de ventas
- Limpieza de columnas y normalización de nombres
- Manejo de valores nulos y duplicados
- Análisis estadístico descriptivo
- Transformación de fechas y creación de variables temporales
- Filtrado y eliminación de columnas no informativas
- Exportación del dataset limpio

**Resultados clave:**
- Dataset de ventas procesado y limpio
- Identificación de outliers y patrones en datos
- Variables temporales agregadas (año, mes, month_name)
- Eliminación de columnas constantes (typeline, amountdiscount)

### 2. 02-Analisis_presupuesto.ipynb
**Objetivo:** Análisis y limpieza del dataset de presupuesto

**Procesos realizados:**
- Carga y exploración de datos de presupuesto
- Transformación de formato ancho a largo (melt)
- Conversión de nombres de meses a números
- Creación de variables temporales
- Análisis estadístico descriptivo
- Visualización de distribuciones y boxplots
- Exportación del dataset limpio

**Resultados clave:**
- Dataset de presupuesto transformado a formato largo
- Variables temporales estandarizadas
- Análisis de distribución de valores presupuestarios
- Dataset listo para fusión con datos de ventas

### 3. 03-Analisis_ventas_presupuesto.ipynb
**Objetivo:** Fusión de datasets y análisis comparativo

**Procesos realizados:**
- Carga de datasets limpios previos
- Fusión inteligente de ventas y presupuesto
- Manejo de combinaciones no coincidentes
- Creación de métricas de comparación
- Análisis estadístico combinado
- Visualización de distribuciones y outliers

**Resultados clave:**
- Dataset final con todas las columnas de ventas + datos de presupuesto
- Métricas de desempeño (diferencia, ratio, cumplimiento)
- Análisis de desviaciones presupuesto vs real
- Dataset listo para dashboard e informe

## Datos del Proyecto

### Dataset Final
- **Filas:** >50,000 (cumple requisito mínimo)
- **Columnas:** >20 (cumple requisito mínimo)
- **Variables:** 
  - Todas las columnas originales de ventas
  - Datos de presupuesto agregados
  - Métricas de análisis comparativo

### Variables Clave
- **Ventas:** `ventas_(€)`, `unidades`, `fecha`, `cliente`
- **Presupuesto:** `presupuesto_mes`, `tipo_cliente`
- **Comparación:** `dif_ventas_presupuesto`, `ratio_ventas_presupuesto`, `cumplimiento_presupuesto`
- **Categorización:** `macrofamilia`, `familia`, `subfamilia`

## Herramientas Utilizadas

- **Python 3.x**
- **Pandas** - Manipulación y análisis de datos
- **Jupyter Notebook** - Desarrollo interactivo
- **Matplotlib/Seaborn** - Visualizaciones
- **VS Code** - Entorno de desarrollo


## 📊 Dashboard en Power BI

Este dashboard interactivo permite visualizar el desempeño de ventas en comparación con el presupuesto por subfamilia de artículo. Incluye métricas clave, gráficos interactivos y filtros para explorar los datos.

### 🛠️ Visualizaciones Incluidas

- **KPIs principales**:
  - **Ventas Totales (€)**: Valor total de ventas.
  - **% Cumplimiento del Presupuesto**: Relación entre ventas y presupuesto.
  - **Margen Bruto Total (€)**: Beneficio bruto (ventas - coste).
- **Gráficos**:
  - **Línea**: Evolución de `Ventas` vs `Presupuesto` por mes.
  - **Barras**: `Ventas` por `subfamilia`.
  - **Circular**: Distribución de `Ventas` por `macrofamilia`.
  - **Medidor**: `% Cumplimiento` global.
- **Filtros interactivos**:
  - `Empresa`, `Mes`, `Subfamilia`.

### 🔍 Hallazgos Clave del Análisis

- **Mayor desviación positiva**: La subfamilia **FLOTADOR LING-LINE** superó su presupuesto en **94290 €** en el mes de **NOVIEMBRE**.
- **Mayor desviación negativa**: La subfamilia **BIN EPE** se quedó por debajo del presupuesto en **-87219,6 €** en el mes de **DICIEMBRE**.
- **Mes con mayor cumplimiento**: El mes de **DICIEMBRE** tuvo el mayor cumplimiento del presupuesto con un **1089,25**.
- **Mayor contribución por macrofamilia**: La macrofamilia **ENVASES Y EMBALAJES** representa el **12361451,41** del total de ventas.

### 📌 Recomendaciones

- Impulsar las subfamilias con bajo rendimiento.
- Revisar la planificación presupuestal en categorías con desviaciones constantes.

### 📁 Archivo del Dashboard

- **Nombre del archivo**: `dashboardeda.pbix`
- **Ubicación**: Carpeta `dashboardeda/` en el repositorio.

## Autores
Susana Mariño Pouso

## Licencia

Este proyecto está destinado a fines educativos.
