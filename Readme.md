# **Telecom X - Análisis de Evasión de Clientes**

## 📝 **Descripción**

Realamos un análisis de datos sobre la cancelación de clientes (Churn) en la empresa **Telecom X**. El proyecto se enfoca en comprender los factores que llevan a los clientes a cancelar sus servicios, con el objetivo de proporcionar información valiosa para el desarrollo de estrategias de retención.

El análisis se realiza utilizando Python y sus principales bibliotecas de manipulación y visualización de datos. Se continúa un proceso de **ETL (Extracción, Transformación y Carga)** para preparar los datos, seguido de un **Análisis Exploratorio de Datos (EDA)** para descubrir patrones e insights.

### ✅ **Objetivos del Proyecto**

- Importar y manipular datos desde una API de manera eficiente.
- Aplicar un proceso de ETL para limpiar y preparar los datos para el análisis.
- Crear visualizaciones estratégicas para identificar patrones y tendencias de evasión.
- Realizar un Análisis Exploratorio de Datos (EDA) y generar un informe con insights relevantes.

---

## 🛠 **️ Metodología**

### **1. Extracción**

Los datos se extrajeron directamente desde una API en formato JSON.

```python
import pandas as pd

url = 'https://github.com/freedox-cts/challenge-telecom-x/raw/refs/heads/main/TelecomX_Data.json'
df = pd.read_json(url)
```
### **2. Transformación y Limpieza**
Se realizó un riguroso proceso de transformación para asegurar la calidad de los datos:

- **Normalización**: Las columnas con datos anidados en formato de diccionario fueron expandidas a columnas individuales.
- **Estandarización**:<br> 
Se tradujeron los nombres de las columnas al español para mayor claridad (ej. customerID a id_cliente).<br>
Se estandarizaron los valores categóricos (ej. Female a Femenino).
- **Manejo de Inconsistencias**:<br>
Se identificaron y corrigieron valores con espacios en blanco en la columna pago_total, imputándolos a partir del pago_mensual y la antiguedad para clientes nuevos.<br>
Se unificaron respuestas binarias (Yes/No) y categorías como "No phone service" a un formato numérico (1/0).
- **Conversión de Tipos de Datos**: Se ajustaron los tipos de datos de las columnas a formatos numéricos (int64, float64) para facilitar el análisis cuantitativo.
- **Ingeniería de Características** (Feature Engineering): Se creó la columna cuentas_diarias a partir del pago_mensual para obtener una métrica de costo a corto plazo.

El dataset limpio y procesado fue guardado como TelecomX_Data_intervenido.csv.

### **3. Carga y Análisis (EDA)**
Se realizó un análisis exploratorio para visualizar la distribución de los datos y las relaciones entre las variables, centrándose en el impacto sobre la cancelacion (Churn).

- **Tasa de Cancelación**: Se encontró una tasa de cancelación general del 25.7%.

- **Análisis por Antigüedad**: Se observa una alta tasa de cancelación en los primeros meses de contrato, la cual disminuye a medida que aumenta la antigüedad del cliente.

- **Análisis por Características Demográficas**: La cancelación es mayor en clientes menores de 65 años, sin pareja y sin dependientes. El género no parece ser un factor determinante.

- **Análisis por Servicios y Contrato**:<br>
Los clientes con contrato mensual tienen una probabilidad de cancelación mucho mayor que aquellos con contratos anuales.<br>
El servicio de Fibra Óptica está asociado a una tasa de cancelación más alta.<br>
El cheque electrónico es el método de pago más común entre los clientes que cancelan.

- **Análisis de Correlación**:<br>
Correlación Inversa (a menor valor, mayor cancelación): antiguedad, contrato, pago_total. Los clientes más nuevos y con contratos a corto plazo tienden a cancelar más.<br>
Correlación Directa (a mayor valor, mayor cancelación): pago_mensual, boleta_electronica. Clientes con pagos mensuales más altos son más propensos a cancelar.

## 📄 **Informe y Conclusiones Principales**
Perfil del Cliente con Alta Probabilidad de Cancelación
- **Antigüedad**: Cliente nuevo (especialmente en los primeros 10 meses).
- **Contrato**: Contrato de tipo mensual.
- **Servicios**: Posee Fibra Óptica, pero carece de servicios adicionales de valor como seguridad_online o serv_tecnico.
- **Pagos**: Tiene un pago_mensual elevado y utiliza el cheque electrónico como método de pago.
- **Demografía**: Generalmente no es mayor de 65 años, no tiene pareja ni dependientes.

**Recomendaciones Estratégicas**
- **Fidelización Temprana**: Crear campañas de retención enfocadas en clientes durante sus primeros meses.
- **Incentivar Contratos a Largo Plazo**: Ofrecer descuentos o beneficios para migrar de contratos mensuales a anuales.
- **Revisar Oferta de Fibra Óptica**: Analizar la calidad y el precio del servicio de Fibra Óptica, ya que está asociado con una alta evasión.
- **Promover Servicios Adicionales**: Incentivar la contratación de servicios de soporte y seguridad, que muestran una fuerte correlación con la retención.

## ⚙️ **Tecnologías Utilizadas**
- Python 3
- Pandas: Para la manipulación y análisis de datos.
- NumPy: Para operaciones numéricas.
- Matplotlib y Seaborn: Para la creación de visualizaciones estáticas.
- Plotly: Para la creación de gráficos interactivos.
- Jupyter Notebook: Como entorno de desarrollo.

**Powered by AAF**