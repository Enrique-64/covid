## Análisis COVID-19 con OWID

## Descripción

Proyecto de análisis de datos del COVID‑19 utilizando Python y Jupyter Lab a partir de los datasets de Our World in Data (OWID).

## Estructura

- `notebooks/`
  - **1_v1_Exploracion_Datos.ipynb**: comparación de varias fuentes de datos y elección de OWID.
  - **2_v3_Exploracion_Datasets_OWID.ipynb**: exploración de todos los datasets OWID relacionados con COVID‑19 y selección de los más relevantes.
  - **3_1_v2_Dataset_covid.ipynb**: procesamiento completo del dataset más importante de OWID sobre el COVID-19:
    1. Limpieza y filtrado de variables
    2. Creación de nuevas variables
    3. Tratamiento de valores nulos y ceros
    4. Visualización exploratoria
    5. Codificación de variables categóricas y escalado de numéricas
    6. Cálculo y limpieza de correlaciones
    7. Generación del dataset final

- `data/dataframes/`
  - Datasets originales de OWID (formato pickle)
  - Resumen de los datasets originales (`resumen_datasets.csv`)
  - Dataset procesado (`_encoded`, formato pickle)

- `LICENSE`
  Licencia MIT.

- `README.md`
  Guía de uso y descripción.

## Requisitos

- Python 3.12
- Jupyter Lab
- Dependencias (instalar con `pip install -r requirements.txt`):

  * pandas
  * numpy
  * scipy
  * scikit-learn
  * matplotlib
  * seaborn
  * owid-catalog

## Instalación

**1. Clona el repositorio**
 
 ```bash
 git clone https://github.com/Enrique-64/covid.git
 cd covid
 ```

**2. Instala dependencias**

 ```bash 
 pip install -r requirements.txt
 ```

**3. Instalación especial de owid-catalog**

**Importante**: `pip install owid-catalog` no funciona con Jupyter Lab; para instalar owid-catalog hay que ejecutar el siguiente código desde un notebook de Jupyter Lab:

```python
import sys
import subprocess

# verifica dónde está instalado Python
print("Python que usa JupyterLab:", sys.executable)

# instala owid-catalog en este Python específico
try:
    subprocess.check_call([sys.executable, '-m', 'pip', 'install', 'owid-catalog'])
    print("✅ Instalación completada")
except Exception as e:
    print("❌ Error en la instalación:", e)

# comprueba si owid-catalog está instalado
result = subprocess.run([sys.executable, '-m', 'pip', 'show', 'owid-catalog'], 
                       capture_output=True, text=True)
print("Paquete instalado:", "owid-catalog" in result.stdout)

# lista paquetes instalados que contengan 'owid'
result = subprocess.run([sys.executable, '-m', 'pip', 'list'], 
                       capture_output=True, text=True)
owid_packages = [line for line in result.stdout.split('\n') if 'owid' in line.lower()]
print("Paquetes owid encontrados:", owid_packages)
```

## Uso

1. Abre Jupyter Lab

 ```bash
 jupyter lab
 ```

2. Ejecuta los notebooks en orden:

- 1_v1_Exploracion_Datos.ipynb
- 2_v3_Exploracion_Datasets_OWID.ipynb
- 3_1_v2_Dataset_covid.ipynb

## Resultados

- Análisis comparativo de fuentes de datos
- Gráficos exploratorios de los datos COVID-19
- Dataset limpio y escalado: `data/dataframes/covid__covid_yyyy-mm-dd_encoded_yyyy-mm-dd.pkl`
- Mapa de correlaciones final

## Autor

**Enrique** – [listas.emo@gmail.com] – GitHub

Licencia MIT © 2025 Enrique
