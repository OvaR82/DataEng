# Diseño de Base de Datos y Consultas SQL

Este repositorio contiene un conjunto de datos de marketing bancario y un script en Python que realiza varias operaciones de procesamiento de datos y consultas SQL en una base de datos SQLite en memoria. A continuación, se presenta una descripción de las principales operaciones realizadas en el script:

## Configuración

El script comienza importando las bibliotecas necesarias y leyendo el conjunto de datos desde un archivo CSV llamado `bank_marketing.csv`. A continuación, se realiza una división de los datos en tres DataFrames: `client`, `campaign` y `economics`, que contienen información sobre los clientes, la campaña de marketing y datos económicos, respectivamente.

## Limpieza de Datos y Renombrado de Columnas

### Limpieza de Datos en el DataFrame `client`

- Se renombran las columnas `client_id` a `id` y `education` a `education`.
- Se eliminan los puntos de la columna `education` y se reemplaza 'unknown' con valores nulos (NaN).
- Se eliminan los puntos de la columna `job`.

### Limpieza de Datos en el DataFrame `campaign`

- Se convierten las categorías 'success' y 'failure' en columnas binarias en la columna `previous_outcome`, y 'nonexistent' se convierte en valores nulos (NaN).
- Se convierten las categorías 'yes' y 'no' en columnas binarias en la columna `campaign_outcome`.
- Se agrega una columna llamada `campaign_id` con valor constante igual a 1.
- La columna `month` se convierte en valores numéricos utilizando un diccionario de mapeo.
- Se crea una columna `last_contact_date` a partir de las columnas `month` y `day`, representando la fecha de último contacto en formato de fecha.

### Limpieza de Datos en el DataFrame `economics`

- Se renombran las columnas `euribor3m` a `euribor_three_months` y `nr_employed` a `number_employed`.

## Exportación de Datos

Los tres DataFrames (`client`, `campaign` y `economics`) se exportan a archivos CSV separados llamados `client.csv`, `campaign.csv` y `economics.csv`, respectivamente.

## Creación de Tablas en PostgreSQL

El script incluye la definición de tablas SQL para PostgreSQL: `client_table`, `campaign_table` y `economics_table`. Cada tabla se crea con sus respectivas columnas y restricciones de clave primaria y referencia. Luego, se cargan datos en estas tablas desde los archivos CSV correspondientes.

## Consultas SQL en SQLite (en memoria)

Se crea una base de datos SQLite en memoria y se cargan los DataFrames (`client`, `campaign` y `economics`) en tablas SQL dentro de la base de datos. Luego, se crean y ejecutan varias consultas SQL.

## Resultados de las Consultas

Los resultados de las dos consultas SQL se almacenan en DataFrames y se imprimen en la consola.

Para ejecutar este script y realizar las operaciones mencionadas, asegúrate de que tengas instaladas las bibliotecas de Python necesarias y el archivo `bank_marketing.csv` en el mismo directorio que el script. También, puedes ajustar las consultas SQL según tus necesidades.