# telecom-analysis.
📊 Análisis Exploratorio y Segmentación de Clientes — ConnectaTel

🎯 Objetivo del Proyecto

Analizar el comportamiento de consumo y el perfil demográfico de los usuarios de ConnectaTel mediante un Análisis Exploratorio de Datos (EDA), tratamiento estadístico de valores atípicos (outliers) y segmentación de clientes. El propósito es traducir los patrones de uso (llamadas, mensajes, minutos y edad) en hallazgos accionables para optimizar la oferta de planes (Básico vs. Premium) y diseñar estrategias de retención y upselling.

📁 Datasets Utilizados

El análisis parte de tres fuentes de datos en formato CSV dentro de la carpeta /datasets/, que posteriormente se integran en la tabla consolidada user_profile:

/datasets/plans.csv (variable plans): Catálogo de planes ofrecidos por ConnectaTel (Básico y Premium) y sus características principales.

/datasets/users_latam.csv (variable users): Información demográfica y contractual de los 4,000 usuarios registrados (user_id, age, plan).

/datasets/usage.csv (variable usage): Registros de actividad y consumo por usuario (cant_mensajes, cant_llamadas, cant_minutos_llamada), con cobertura de 3,999 usuarios activos (identificando 1 usuario sin registros de uso).

Tabla consolidada (user_profile): DataFrame resultante de integrar perfil y consumo, enriquecido con las variables categóricas de segmentación grupo_uso y grupo_edad.

🔍 Etapas del Análisis Realizadas

Carga, Exploración Inicial e Integración de Datos:

Importación de librerías (pandas, numpy, seaborn, matplotlib.pyplot).

Carga de /datasets/plans.csv, /datasets/users_latam.csv y /datasets/usage.csv en los DataFrames plans, users y usage, e inspección inicial con .head(), .info(), .isna().sum() y .describe().

Integración de la información de perfil y actividad en user_profile (4,000 registros demográficos y 3,999 registros con actividad).

Análisis Exploratorio de Datos (EDA) y Distribuciones:

Evaluación de medidas de tendencia central, dispersión y posición (mean, median, std, cuartiles Q1–Q3).

Visualización mediante histogramas y diagramas de caja (boxplots) para age, cant_mensajes, cant_llamadas y cant_minutos_llamada.

Detección y Tratamiento de Outliers (Método IQR):

Cálculo de límites intercuartílicos ($Q3 + 1.5 \times \text{IQR}$) y contraste con valores máximos (cant_mensajes máx. 17, cant_llamadas máx. 15, cant_minutos_llamada máx. 155.69 min).

Decisión: Conservar los outliers superiores por corresponder a clientes reales de alto consumo, priorizando métricas robustas (mediana e IQR) sobre la media.

Segmentación de Clientes y Visualización:

Por nivel de uso (grupo_uso): Clasificación en Bajo uso (< 5 llamadas y < 5 mensajes), Uso medio (< 10 llamadas y < 10 mensajes) y Alto uso (resto de casos).

Por edad (grupo_edad): Clasificación en Joven (< 30 años), Adulto (30–59 años) y Adulto Mayor (≥ 60 años).

Gráficos de frecuencia (sns.countplot) para analizar la distribución de cada segmento.

Síntesis Ejecutiva y Recomendaciones:

Traducción de hallazgos técnicos a estrategias de upselling hacia Premium (enfocadas en Alto uso y Uso medio en plan Básico) y retención con planes simples (Bajo uso y Adulto Mayor).

💻 Cómo Ejecutar el Notebook

**Opción A: Abrir en Google Colab (Recomendado)**

Abre el notebook (.ipynb) en Google Colab ([https://colab.research.google.com/).](https://colab.research.google.com/github/HectorChona/telecom-analysis./blob/main/S7_Version_Estudiante_Project_ConnectaTel.ipynb)

Asegúrate de que los tres archivos estén disponibles en la ruta /datasets/ (o actualiza las rutas en pd.read_csv() si los subes a /content/ o Google Drive).

En el menú superior, selecciona Entorno de ejecución > Ejecutar todas (Ctrl + F9).

**Opción B: Ejecución Local (Jupyter Notebook / VS Code)
**
Abre una terminal en la carpeta raíz del proyecto.

Inicia Jupyter con jupyter notebook o abre el archivo .ipynb directamente en VS Code.

Ejecuta las celdas de forma secuencial de arriba hacia abajo.

