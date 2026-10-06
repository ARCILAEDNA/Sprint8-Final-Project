# Sprint8-Final-Project
Explorando Drivers de comportamiento en una empresa de retail
# Sprint8-Final-Project
Explorando Drivers de comportamiento en una empresa de retail

## Descripción general

NovaRetail+ es una plataforma de comercio electrónico en Latinoamérica con millones de usuarios. Este proyecto es un análisis correlacional y exploratorio, desarrollado para el equipo de Crecimiento y retención de cara al cierre de 2024, que busca responder una pregunta central: ¿qué factores del comportamiento del cliente están más fuertemente asociados con el ingreso anual generado? A lo largo de todo el trabajo se mantiene un principio rector: correlación no implica causalidad. Los resultados describen asociaciones entre variables y no efectos.

## Conjunto de datos

El análisis utiliza el archivo `novaretail_comportamiento_clientes_2024.csv`, que contiene 15,000 registros y 12 columnas, sin valores nulos. Cada fila corresponde a un cliente e incluye su identificador (`id_cliente`), su edad (`edad`), su ingreso anual estimado (`nivel_ingreso`), el número de visitas y de compras en el mes (`visitas_mes` y `compras_mes`), el gasto en anuncios asignado al usuario (`gasto_publicidad_dirigida`), su calificación de satisfacción en una escala del 1 al 5 (`satisfaccion`), si es miembro premium (`miembro_premium`), si abandonó la plataforma (`abandono`), el tipo de dispositivo (`tipo_dispositivo`: móvil, escritorio o tablet), la región (`region`: norte, sur, este u oeste) y el ingreso anual generado por el cliente para la empresa (`ingreso_anual`), que es la métrica principal del estudio. El archivo de datos no se incluye en este repositorio; el notebook lo carga desde la ruta `/datasets/novaretail_comportamiento_clientes_2024.csv`, por lo que esta ruta debe ajustarse según el entorno de ejecución.

## Metodología

El proyecto se organiza en seis secciones. La primera carga el dataset y valida su estructura, sus tipos de datos y sus rangos generales. La segunda prepara los datos y documenta los supuestos; en ella se corrige el tipo de dato de `edad` de `float64` a `int64`, se describen las variables numéricas, binarias y categóricas, y se declara que el análisis emplea todo el conjunto de datos disponible. La tercera visualiza las relaciones mediante un heatmap de correlaciones y diagramas de dispersión para los pares clave, y justifica por qué no se genera un scatterplot general. La cuarta cuantifica las relaciones con el coeficiente adecuado para cada tipo de variable: Pearson para relaciones lineales entre variables numéricas, Spearman para relaciones monótonas sin supuesto de normalidad, punto-biserial para relaciones entre una variable numérica y una binaria, y V de Cramér para asociaciones entre variables categóricas. La quinta interpreta los resultados para el negocio y la sexta expone las limitaciones y los próximos pasos.

## Principales hallazgos

El primer hallazgo es que las compras mensuales presentan la asociación más fuerte con el ingreso anual, con una correlación de Pearson de 0,967. Una relación tan intensa sugiere que ambas variables podrían medir en buena medida lo mismo, por lo que se recomienda validar con el equipo de datos la definición de `ingreso_anual` antes de usar una variable para explicar la otra en un modelo.

El segundo hallazgo es que las visitas mensuales y el gasto en publicidad dirigida muestran asociaciones positivas, pero de menor magnitud, con el ingreso anual. 

El tercer hallazgo es que ser miembro premium presenta una asociación débil, aunque estadísticamente significativa, con el ingreso anual.

## Limitaciones y próximos pasos

Los coeficientes utilizados solo capturan relaciones lineales o monótonas, por lo que no detectan patrones no lineales ni interacciones. La variable `ingreso_anual` tiene una distribución fuertemente sesgada a la derecha, con al menos el 25 % de los registros en cero, lo que puede influir en los coeficientes. Los datos son una fotografía del cierre de 2024, sin dimensión temporal, y no se evaluó directamente la relación de región y tipo de dispositivo con el ingreso anual, ni se trataron los valores atípicos ni se controlaron varias variables de forma simultánea. 
Como próximos pasos se propone segmentar el ingreso anual por región, tipo de dispositivo, frecuencia de compra y estatus premium, analizar por separado a los clientes con ingreso anual igual a cero, ajustar un modelo multivariable cuidando la colinealidad, explorar relaciones no lineales e incorporar la dimensión temporal si se dispone de datos mensuales. 

## Tecnologías utilizadas

El proyecto está desarrollado en Python dentro de un Jupyter Notebook y emplea las librerías pandas, NumPy, seaborn, matplotlib y SciPy.

## Estructura del repositorio

El repositorio contiene el notebook `S8_Student_Version-Project-NovaRetail.ipynb`, que incluye el análisis completo, y este archivo `README.md`.

## Autora

Edna Arcila - www.linkedin.com/in/edna-arcila-avila-7a4063174
