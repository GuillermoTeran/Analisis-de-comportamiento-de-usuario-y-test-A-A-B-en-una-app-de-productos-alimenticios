# Análisis de comportamiento de usuario y test A/A/B en una app de productos alimenticios

## ES Español

Descripción del proyecto:

En este proyecto, trabajé como analista de datos para una startup dedicada a la venta de productos alimenticios a través de su aplicación móvil. El objetivo principal fue comprender cómo los usuarios interactúan con la aplicación y cómo las decisiones de diseño pueden impactar sus comportamientos, específicamente en relación con la conversión de ventas.

## Objetivos principales:
Analizar el embudo de conversión para detectar puntos de fricción en el recorrido del usuario.

Evaluar un experimento A/A/B diseñado para medir el impacto de un cambio en la tipografía de la interfaz.

Validar la correcta segmentación de los grupos de prueba.

Proporcionar recomendaciones basadas en datos para mejorar la experiencia del usuario.

## Datos utilizados:
Dataset: logs_exp_us.csv

Cada registro representa un evento de usuario dentro de la aplicación.

Campos principales:

event_name: tipo de acción realizada por el usuario.

device_id_hash: identificador único del usuario.

event_timestamp: marca de tiempo del evento.

exp_id: grupo experimental (246 y 247 son control; 248 es prueba).

## Paso 1: Lectura y preparación de datos
Se cargaron y revisaron los datos.

Se renombraron columnas para facilitar la lectura.

Se transformaron los tipos de datos y se extrajo la fecha del timestamp.

Se identificaron valores faltantes y se validó su impacto.

## Paso 2: Exploración de datos
Se identificaron 5 eventos y 7551 usuarios únicos.

Promedio de eventos por usuario: 32.28

El rango temporal cubierto fue de 2019-07-25 a 2019-08-07

Al trazar la distribución de eventos por fecha, se observó que los primeros días tenían registros incompletos.

Se estableció una fecha de corte para asegurar integridad de los datos, minimizando el sesgo.

## Paso 3: Análisis del embudo de conversión
Se identificaron los eventos más comunes y su orden lógico en el flujo de usuario.
Ejemplo:

App Launch

Product View

Add to Cart

Checkout

Payment Success

Se calculó la proporción de usuarios que pasaron de una etapa a la siguiente.

Etapa con mayor pérdida: entre Add to Cart y Checkout.

Solo un 47.68% de los usuarios completó el recorrido completo hasta el pago.

Estos resultados destacan áreas críticas para mejoras en la experiencia de usuario o incentivos de conversión.

## Paso 4: Evaluación del test A/A/B
### Validación del test A/A
Se compararon los grupos 246 y 247 (ambos con tipografía original).

Para cada evento:

Se calcularon proporciones de usuarios que realizaron la acción.

Se aplicó una prueba de hipótesis (proporciones) para validar si las diferencias eran significativas.

Resultado: No se detectaron diferencias significativas → segmentación válida.

### Análisis del grupo B (fuente nueva)
Se repitió el análisis para el grupo 248 (fuente nueva), comparándolo con:

Cada grupo de control individualmente.

Ambos grupos de control combinados.

Eventos clave analizados:

Visualización de productos

Agregar al carrito

Finalización de compra

Resultados:

Para algunos eventos, se observó una ligera caída en la interacción con la nueva tipografía.

Sin embargo, la mayoría de las diferencias no fueron estadísticamente significativas.

## Paso 5: Prueba de hipótesis y corrección por comparaciones múltiples
Hipótesis nula (H₀): no hay diferencia entre los grupos.

Hipótesis alternativa (H₁): existe una diferencia significativa entre los grupos.

Nivel de significancia original: α = 0.05.

Se realizaron múltiples pruebas (≈ N pruebas).

Se aplicó la corrección de Bonferroni para controlar el error tipo I:

Nuevo α ajustado: α/N.

Tras el ajuste, las diferencias dejaron de ser significativas → no se pudo concluir que la tipografía nueva afecte el comportamiento del usuario.

## Conclusiones:
El embudo reveló puntos de abandono importantes en la etapa previa al checkout, lo que indica una oportunidad clara de mejora en la conversión.

El experimento A/A/B mostró que:

Los grupos de control fueron consistentes.

El grupo con tipografía nueva no mostró mejoras significativas.

Recomendación: Postergar o repensar el cambio tipográfico, ya que no aporta un beneficio claro y puede introducir riesgo innecesario.

## Herramientas utilizadas:
Python (pandas, matplotlib, seaborn, scipy, statsmodels)

Jupyter Notebook

Estadística inferencial (prueba de proporciones, corrección por comparaciones múltiples)

## Impacto del análisis:
Este análisis proporcionó evidencia crítica para decisiones de producto, ayudando a la empresa a evitar cambios visuales que no aportaban valor al usuario. Asimismo, el embudo permitió identificar cuellos de botella clave en la experiencia de compra, facilitando decisiones más informadas para aumentar la conversión.


# User behavior analysis and A/A/B testing in a food product app

## US English

Project description:

In this project, I worked as a data analyst for a startup dedicated to selling food products through its mobile app. The main objective was to understand how users interact with the app and how design decisions can impact their behavior, specifically about sales conversion.

## Main objectives:
Analyze the conversion funnel to detect friction points in the user journey.

Evaluate an A/A/B experiment designed to measure the impact of a change in the interface typography.

Validate the correct segmentation of the test groups.

Provide data-driven recommendations to improve the user experience.

## Data used:
Dataset: logs_exp_us.csv

Each record represents a user event within the application.

Main fields:

event_name: type of action performed by the user.

device_id_hash: unique user identifier.

event_timestamp: event timestamp.

exp_id: experimental group (246 and 247 are control; 248 is test).

## Step 1: Reading and preparing data
The data was loaded and reviewed.

Columns were renamed to make them easier to read.

Data types were transformed and the timestamp data was extracted.

Missing values were identified and their impact was validated.

## Step 2: Data exploration
Five events and 7,551 unique users were identified.

Average number of events per user: 32.28

The time range covered was from July 25, 2019, to August 7, 2019.

When plotting the distribution of events by date, it was observed that the first few days had incomplete records.

A cut-off date was established to ensure data integrity and minimize bias.

## Step 3: Conversion funnel analysis
The most common events and their logical order in the user flow were identified.
Example:

App Launch

Product View

Add to Cart

Checkout

Payment Success

The proportion of users who moved from one stage to the next was calculated.

Stage with the highest loss: between Add to Cart and Checkout.

Only 47.68% of users completed the entire journey to payment.

These results highlight critical areas for improvements in user experience or conversion incentives.

## Step 4: Evaluation of the A/A/B test
### Validation of the A/A test
Groups 246 and 247 (both with original typography) were compared.

For each event:

The proportions of users who acted were calculated.

A hypothesis test (proportions) was applied to validate whether the differences were significant.

Result: No significant differences were detected → valid segmentation.

### Analysis of group B (new source)
The analysis was repeated for group 248 (new source), comparing it with:

Each control group individually.

Both control groups combined.

Key events analyzed:

Product viewing

Add to cart

Checkout completion

Results:

For some events, a slight drop in interaction was observed with the new typography.

However, most of the differences were not statistically significant.

## Step 5: Hypothesis testing and correction for multiple comparisons
Null hypothesis (H₀): there is no difference between the groups.

Alternative hypothesis (H₁): there is a significant difference between the groups.

Original significance level: α = 0.05.

Multiple tests were performed (≈ N tests).

The Bonferroni correction was applied to control the type I error:

New adjusted α: α/N.

After the adjustment, the differences were no longer significant → it could not be concluded that the new font affects user behavior.

## Conclusions:
The funnel revealed significant drop-off points in the pre-checkout stage, indicating a clear opportunity for conversion improvement.

The A/A/B experiment showed that:

The control groups were consistent.

The group with the new typography did not show significant improvements.

Recommendation: Postpone or rethink the typography change, as it does not provide a clear benefit and may introduce unnecessary risk.

## Tools used:
Python (pandas, matplotlib, seaborn, scipy, statsmodels)

Jupyter Notebook

Inferential statistics (proportion test, correction for multiple comparisons)

## Impact of the analysis:
This analysis provided critical evidence for product decisions, helping the company avoid visual changes that did not add value for the user. The funnel also identified key bottlenecks in the shopping experience, facilitating more informed decisions to increase conversion.








