# README - Transformación de Datos

## Descripción del Proyecto
Este proyecto tiene como objetivo la extracción, limpieza, normalización y análisis exploratorio de datos provenientes de la base de datos `Actividad_ETL`. Los datos fueron transformados y cargados en una nueva tabla denominada `TRANSFORMACION` para su posterior uso en análisis y reportes.

## Requisitos
- Python 3.x
- Librerías necesarias:
  - `pandas`
  - `numpy`
  - `sqlalchemy`
  - `matplotlib`
  - `seaborn`
  - `pyodbc`

## Proceso de ETL

### 1. Extracción de Datos
- Conexión a SQL Server mediante SQLAlchemy.
- Obtención de datos desde la tabla `tabla_etl_nueva1` en la base de datos `Actividad_ETL`.

### 2. Transformación de Datos
- **Estandarización de nombres de columnas:** Conversión a minúsculas y eliminación de caracteres especiales.
- **Manejo de valores nulos:**
  - Columnas categóricas: Reemplazo con "No Registra".
  - Columnas numéricas: Imputación con 0.
  - `edad`: Reemplazo de valores 0 con la mediana.
- **Corrección de tipos de datos:**
  - Conversión de columnas numéricas a `float`.
  - Variables categóricas a `category`.
  - Claves primarias como `string`.
  - `ano` normalizado a `int`.
- **Eliminación de columnas duplicadas:** Se eliminó `a_global` por ser idéntica a `puntaje_global_icfes`.
- **Estandarización de categorías:** Homogeneización de valores en `estado_civil`, `colegio_sector`, y `colegio_clasificacion`.
- **Conversión a mayúsculas:** Todas las cadenas de texto fueron convertidas a mayúsculas.

### 3. Análisis Exploratorio de Datos (EDA)
- Generación de estadísticas descriptivas con `df.describe()`.
- Creación de histogramas y boxplots para identificar distribuciones y valores atípicos.
- Análisis de correlación entre variables numéricas.

### 4. Carga de Datos
- Carga de los datos transformados a SQL en la tabla `TRANSFORMACION`.

## Uso
Ejecutar el script principal para extraer, transformar y cargar los datos. Asegurar que las credenciales de la base de datos estén configuradas correctamente en el script de conexión.

```bash
python transformacion_datos.py
