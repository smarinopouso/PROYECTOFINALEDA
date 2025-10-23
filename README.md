# Proyecto Final: Análisis de Ventas y Presupuesto

## 🔹 Descripción del proyecto

Este proyecto tiene como objetivo realizar un **análisis exploratorio de datos (EDA)** y generar un **dashboard operativo** con datos de ventas y presupuesto de la empresa, usando Python, Pandas y Power BI.  
Se trabajó con **dos fuentes de datos**:

1. **Ventas (CSV)**: contiene información de ventas reales por cliente, artículo y fecha.  
2. **Presupuesto (Excel)**: contiene el presupuesto de ventas por subfamilia y empresa.

Se realizaron las siguientes etapas: limpieza, transformación, análisis descriptivo, cálculo de métricas y preparación del dataset final para Power BI.

---

## 🔹 Estructura de carpetas

PROYECTOFINALEDA/
│
├─ data/
│ ├─ raw/ # Datos originales sin procesar
│ │ ├─ ventas2024.csv
│ │ └─ presupuesto2024.xlsx
│ ├─ output/ # Datos procesados
│ │ ├─ ventas2024_limpio.csv
│ │ ├─ presupuesto2024_limpio.xlsx
│ │ └─ final/
│ │ ├─ df_final_para_powerbi.csv
│ │ └─ df_final_para_powerbi.xlsx
│
├─ notebooks/ # Jupyter notebooks con análisis
│ └─ ProyectoFinal_EDA.ipynb
│
├─ src/ # Scripts Python, funciones y utilidades
│ └─ limpieza_transformacion.py
│
├─ README.md
└─ PROYECTO_POWERBI.pbix # Dashboard final en Power BI

markdown
Copiar código

---

## 🔹 Limpieza y transformación de datos

1. **Homogeneización de columnas**  
   - `codcompany` → `cod_empresa`  
   - `ventas_(€)` → `ventas_presupuesto` (en presupuesto)  
   - Se normalizó el formato de nombres (minúsculas, sin espacios ni caracteres especiales).

2. **Conversión de tipos**  
   - Columna `fecha` convertida a tipo datetime.  
   - Columnas numéricas convertidas a float/int según corresponda.

3. **Manejo de valores nulos y duplicados**  
   - Se revisaron duplicados y se eliminaron registros repetidos por `(cod_empresa, idarticle, fecha)`.  
   - Valores nulos en métricas de comparación (`dif_ventas_presupuesto`, `ratio_ventas_presupuesto`) se mantienen como `NaN` si no hay presupuesto asignado, para reflejar correctamente que no hay datos disponibles.

4. **Transformación de columnas de meses en filas**  
   - En el dataset de presupuesto, las columnas `enero` a `diciembre` se transformaron a formato largo (`mes` y `presupuesto_mes`) usando `pd.melt()`.  
   - Se creó la columna `month_name` con formato `YYYY-MM` para análisis temporal.

---

## 🔹 Merge de datasets

- Se realizó un **merge left** de ventas con presupuesto usando las columnas:  
  `cod_empresa` y `subfamilia`.  
- Esto asegura que **todas las ventas se mantengan**, incluso si no tienen presupuesto asociado.  
- Se calcularon las métricas:  
  - `dif_ventas_presupuesto = ventas_(€) - presupuesto_mes`  
  - `ratio_ventas_presupuesto = ventas_(€) / presupuesto_mes`  
- Las métricas muestran `NaN` cuando no hay presupuesto para la venta correspondiente, lo cual es esperado.

---

## 🔹 Análisis descriptivo

- Estadísticas básicas de columnas numéricas: `mean`, `min`, `max`, `std`.  
- Frecuencia de categorías: `macrofamilia`, `familia`, `subfamilia`.  
- Histogramas y boxplots para detectar outliers en ventas, presupuesto, diferencia y ratio.

---

## 🔹 Dataset final

- `df_final_para_powerbi.csv` y `df_final_para_powerbi.xlsx`  
- Columnas principales:

cod_empresa | idcustomer | fecha | idarticle | unidades | ventas_(€) | ventas_presupuesto | dif_ventas_presupuesto | ratio_ventas_presupuesto | macrofamilia | familia | subfamilia | month_name | year | month

yaml
Copiar código

- Listo para **Power BI**, sin eliminar ventas, con métricas calculadas y NaN donde no hay presupuesto.

---

## 🔹 Power BI

- Se creó un **dashboard interactivo** que incluye:  
  - KPIs de total ventas, total presupuesto, diferencia y ratio promedio.  
  - Gráficos de barras comparando ventas vs presupuesto por macrofamilia, familia y subfamilia.  
  - Gráficos de líneas mostrando evolución temporal por `month_name`.  
  - Filtros (slicers) por empresa, año, macrofamilia, familia y subfamilia.

- El dashboard permite analizar **cumplimiento de presupuesto**, detectar subfamilias con desviaciones y realizar seguimiento mensual de ventas.

---

## 🔹 Conclusión

- El proyecto muestra un **flujo completo de EDA y preparación de datos** para análisis y visualización.  
- Todas las métricas y datos están preparados para ser utilizados en **Power BI**, cumpliendo con los requisitos del proyecto final.  
- La carpeta `src` contiene scripts reutilizables para limpieza, transformación y cálculo de métricas, facilitando reproducir el proceso.