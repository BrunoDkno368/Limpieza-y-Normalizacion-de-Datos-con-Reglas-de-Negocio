📊 Proyecto ETL con Python y Pandas – Limpieza y Normalización de Datos Bancarios
📌 Descripción general

Este proyecto implementa un proceso ETL (Extract, Transform, Load) completo utilizando Python, Pandas y expresiones regulares, aplicado a un dataset bancario con datos sucios, inconsistentes y no estructurados.

El objetivo principal es transformar datos crudos en un dataset limpio, consistente y apto para análisis, respetando reglas de negocio reales del sector bancario.

El proyecto fue desarrollado en Google Colab y está orientado a demostrar habilidades prácticas en:

Data Cleaning

Data Quality

Validaciones de negocio

Transformaciones complejas

Pensamiento analítico aplicado a ETL

🧰 Tecnologías utilizadas

Python

Pandas

NumPy

Regex (re)

Google Colab

🗂️ Estructura del proceso ETL

1️⃣ Extract (E)

Lectura de un archivo CSV con múltiples inconsistencias:

Tipos de datos incorrectos

Valores nulos

Errores semánticos

Formatos mixtos

Valores fuera de rango

df = pd.read_csv('banco_dataset_sucio.csv')

2️⃣ Transform (T)

La etapa principal del proyecto.
Cada columna fue tratada de forma independiente, aplicando reglas de negocio explícitas.

🔹 Limpieza y decisiones por columna

🆔 id_cliente

Reglas de negocio

No nulo

Único

Tipo entero

Decisiones

Eliminación de registros nulos

Conversión explícita a int

Verificación de duplicados

Motivo
Clave primaria del dataset. No se permite ambigüedad ni pérdida de integridad.

👤 nombre

Problemas detectados

Símbolos especiales (@, !)

Espacios mal formateados

Valores nulos

Palabras cortadas (Mar ia)

Acciones

Conversión a StringDtype

Limpieza con regex

Normalización de espacios

Correcciones semánticas

Capitalización

Imputación controlada: "Sin datos"

Motivo
Garantizar consistencia textual sin eliminar registros.

🎂 edad

Reglas

Rango válido: 18–100

No texto

No valores negativos

Regla bancaria: no se opera con menores

Acciones

Mapeo semántico (treinta → 30)

Conversión a numérico con errors='coerce'

Valores fuera de rango → NaN

Imputación con mediana

Conversión final a entero

Motivo
Evitar sesgos y mantener coherencia estadística.

📧 email

Reglas

Debe contener @ y dominio válido

Emails inválidos → NaN

Emails duplicados permitidos

Acciones

Normalización a minúsculas

Validación con regex

Uso de na=False para evitar errores

Imputación con "Sin datos"

Motivo
Campo informativo, no clave. Se prioriza limpieza sobre eliminación.

💰 saldo_cuenta

Reglas

No texto

No negativo

Máximo: 10.000.000

Problemas

Separadores mixtos (. y ,)

Valores extremos

Texto (abc)

Acciones

Normalización de separadores

Conversión a numérico

Validación de rango

Outliers → NaN

Imputación con mediana

Motivo
Evitar distorsión financiera y preservar distribución.

🏦 tipo_cuenta

Valores permitidos

Caja Ahorro

Cuenta Corriente

Acciones

Normalización a minúsculas

Mapeo semántico (CA, CC, CajaAhorro, etc.)

Valores desconocidos → "Sin Datos"

Capitalización final

Motivo
Estandarización categórica para análisis y reporting.

📅 fecha_alta

Problemas

Múltiples formatos

Fechas inválidas

Fechas inexistentes

Texto con meses en español

Acciones

Traducción de meses

Parsing múltiple

Correcciones estructurales

Conversión a datetime

Fechas inválidas → NaT

Imputación controlada

Motivo
Preservar la mayor cantidad de fechas válidas posibles sin errores silenciosos.

🚦 estado_cliente

Valores permitidos

Activo

Inactivo

Suspendido

Acciones

Normalización de texto

Capitalización

Valores nulos → Inactivo / Sin Datos

Motivo
Campo categórico clave para segmentación.

3️⃣ Load (L)

Exportación del dataset limpio para análisis posterior:

df.to_csv('datos_limpios.csv', index=False)

❓ Preguntas clave surgidas durante el proceso

Durante el desarrollo del ETL surgieron preguntas técnicas relevantes que guiaron decisiones de diseño:

¿Cuándo usar astype(str) vs astype("string")?

¿Por qué usar na=False en validaciones con .str.match()?

¿Cuándo imputar con media y cuándo con mediana?

¿Es correcto reemplazar datos inválidos o es mejor eliminarlos?

¿Cómo manejar fechas con múltiples formatos sin perder información?

¿Cómo evitar errores silenciosos en parsing de fechas?

Estas preguntas fueron fundamentales para aplicar buenas prácticas de Data Engineering.

🎯 Conclusiones

Este proyecto demuestra:

Capacidad para diseñar ETL de punta a punta

Aplicación de reglas de negocio reales

Uso correcto de Pandas avanzado

Pensamiento crítico en decisiones de limpieza

Enfoque profesional orientado a Data Analyst / Data Engineer Jr


👤 Autor
Bruno Argañaraz Analista de Datos Tucumán, Argentina

LinkedIn: https://www.linkedin.com/in/bruno-arga%C3%B1araz-726a4a199/
🔑

ETL, Python, Pandas, Data Cleaning, Data Quality,
Data Analyst, Data Engineering, Regex, Business Rules,
Data Transformation, Data Wrangling, Google Colab,
CSV Processing, Banking Dataset
