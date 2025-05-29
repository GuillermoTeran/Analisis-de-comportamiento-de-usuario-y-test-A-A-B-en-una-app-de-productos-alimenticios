# Análisis de comportamiento de usuario y test A/A/B en una app de productos alimenticios
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
Se identificaron más de XXX eventos y YYY usuarios únicos.

Promedio de eventos por usuario: Z.XX.

El rango temporal cubierto fue de YYYY-MM-DD a YYYY-MM-DD.

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

Solo un X% de los usuarios completó el recorrido completo hasta el pago.

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

Impacto del análisis:
Este análisis proporcionó evidencia crítica para decisiones de producto, ayudando a la empresa a evitar cambios visuales que no aportaban valor al usuario. Asimismo, el embudo permitió identificar cuellos de botella clave en la experiencia de compra, facilitando decisiones más informadas para aumentar la conversión.
