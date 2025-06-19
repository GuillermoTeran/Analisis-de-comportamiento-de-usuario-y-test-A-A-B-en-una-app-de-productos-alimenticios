# 📱 Caso de Estudio: Análisis del Comportamiento de Usuario y Test A/A/B en una App de Productos Alimenticios

## 🇪🇸 Español

### Descripción del Proyecto  
Trabajé como analista de datos para una startup dedicada a la venta de productos alimenticios a través de su aplicación móvil. El objetivo fue comprender el comportamiento de los usuarios y evaluar cómo un cambio en el diseño (tipografía) afecta la conversión en la app.

### Objetivos del Proyecto
- Analizar el embudo de conversión para detectar puntos de fricción.
- Evaluar un experimento A/A/B relacionado con un cambio en la tipografía.
- Validar la correcta segmentación de los grupos de prueba.
- Proporcionar recomendaciones basadas en datos para mejorar la conversión.

### Fuente de Datos

| Dataset           | Descripción                                  |
|-------------------|----------------------------------------------|
| `logs_exp_us.csv` | Registro de eventos de usuario en la app     |

**Variables clave:**  
- `event_name`: tipo de acción del usuario  
- `device_id_hash`: identificador único de usuario  
- `event_timestamp`: fecha y hora del evento  
- `exp_id`: grupo experimental (246 y 247 = control, 248 = prueba)

---

### 🔎 Análisis Exploratorio

#### Paso 1: Lectura y Preparación de Datos
- Carga y limpieza inicial.
- Renombramiento de columnas.
- Conversión de tipos y extracción de fecha.
- Revisión de valores nulos.

#### Paso 2: Exploración de Datos
- 7,551 usuarios únicos y 5 eventos principales.
- Promedio: **32.28 eventos por usuario**.
- Rango temporal: **2019-07-25 a 2019-08-07**.
- Se detectaron registros incompletos al inicio, por lo que se aplicó una **fecha de corte** para minimizar sesgos.

---

### 🔁 Análisis del Embudo de Conversión

**Flujo identificado:**
1. App Launch  
2. Product View  
3. Add to Cart  
4. Checkout  
5. Payment Success

- Se calculó la proporción de usuarios que avanzaron entre etapas.
- Mayor pérdida: entre **Add to Cart → Checkout**.
- Solo **47.68%** de los usuarios completó el flujo completo.

🔔 *Implicación:* Puntos críticos de abandono antes del pago → oportunidad para mejoras en UX o incentivos de conversión.

---

### 🧪 Evaluación del Test A/A/B

#### Validación del Test A/A
- Comparación entre grupos 246 y 247 (tipografía original).
- Se aplicaron pruebas de proporciones para cada evento.
- ✅ Resultado: **sin diferencias significativas** → segmentación válida.

#### Evaluación del Grupo B (tipografía nueva)
- Comparación del grupo 248 contra:
  - Cada grupo de control por separado
  - Grupos de control combinados
- Eventos clave: visualización de productos, agregar al carrito, completar compra.
- Resultado:  
  - **Ligera caída en interacción** en algunos eventos con la nueva fuente.  
  - Diferencias **no significativas estadísticamente** en la mayoría de los casos.

---

### 📊 Prueba de Hipótesis y Corrección por Comparaciones Múltiples

- H₀: No hay diferencia entre los grupos.  
- H₁: Hay diferencias significativas.  
- α original: 0.05  
- Se realizaron múltiples pruebas → se aplicó **corrección de Bonferroni**.  
- Nuevo α ajustado: α / N  
- 🔍 Resultado final: **las diferencias dejaron de ser significativas tras la corrección**.

---

### ✅ Conclusiones
- El embudo evidenció puntos de fuga importantes antes del pago → se deben optimizar esas etapas.
- El test A/A/B demostró:
  - Segmentación correcta en los grupos de control.
  - El cambio de tipografía **no generó mejoras significativas**.
- **Recomendación:** Postergar o reconsiderar el cambio de diseño visual, ya que podría suponer un riesgo sin retorno claro.

---

### 🛠️ Herramientas Utilizadas
- Python (pandas, matplotlib, seaborn, scipy, statsmodels)
- Jupyter Notebook
- Estadística inferencial: prueba de proporciones, corrección Bonferroni

---

### 📈 Impacto del Análisis
- Se evitó implementar un cambio visual sin beneficios claros.
- Se identificaron cuellos de botella en el recorrido de compra.
- Se proporcionaron insights para decisiones informadas sobre diseño y conversión.

---

## 🇺🇸 English

# 📱 Case Study: User Behavior Analysis and A/A/B Testing in a Food Product App

### Project Description  
I worked as a data analyst for a startup focused on selling food products through a mobile app. The goal was to understand user behavior and assess how a design change (typography) affects conversion.

### Project Objectives
- Analyze the conversion funnel to identify friction points.
- Evaluate an A/A/B experiment related to a typography change.
- Validate proper segmentation of experimental groups.
- Provide data-driven recommendations for improving conversion.

### Data Source

| Dataset           | Description                                  |
|-------------------|----------------------------------------------|
| `logs_exp_us.csv` | User event logs from the app                 |

**Key variables:**  
- `event_name`: type of user action  
- `device_id_hash`: unique user identifier  
- `event_timestamp`: event timestamp  
- `exp_id`: experimental group (246 and 247 = control; 248 = test)

---

### 🔎 Exploratory Analysis

#### Step 1: Data Loading and Preparation
- Initial data load and review.
- Renamed columns for clarity.
- Converted data types and extracted dates.
- Handled and validated missing values.

#### Step 2: Data Exploration
- Identified **7,551 unique users** and 5 main events.
- Average: **32.28 events per user**.
- Time range: **July 25 to August 7, 2019**.
- Early days had incomplete data → applied a **cutoff date** to ensure data integrity.

---

### 🔁 Conversion Funnel Analysis

**User flow identified:**
1. App Launch  
2. Product View  
3. Add to Cart  
4. Checkout  
5. Payment Success

- Calculated drop-off rates between each step.
- Highest loss occurred between **Add to Cart → Checkout**.
- Only **47.68%** of users completed the full journey to payment.

🔔 *Implication:* Critical friction before checkout → opportunities to optimize UX and increase conversion.

---

### 🧪 A/A/B Test Evaluation

#### A/A Test Validation
- Compared groups 246 and 247 (original typography).
- Applied proportion tests for each event.
- ✅ Result: **no significant differences** → segmentation is valid.

#### Test Group B (New Typography)
- Compared group 248 with:
  - Each control group separately
  - Both control groups combined
- Key events analyzed: product views, add to cart, purchase completion.
- Result:  
  - **Slight drop in engagement** for some events with the new font.  
  - Most differences were **not statistically significant**.

---

### 📊 Hypothesis Testing and Multiple Comparison Correction

- H₀: No difference between groups.  
- H₁: Significant difference exists.  
- Original α: 0.05  
- Multiple tests conducted → **Bonferroni correction applied**  
- Adjusted α: α / N  
- 🔍 Final result: **differences became non-significant after correction**

---

### ✅ Conclusions
- Funnel revealed major drop-offs before checkout → requires optimization.
- A/A/B experiment showed:
  - Control groups behaved consistently.
  - New typography **did not improve performance significantly**.
- **Recommendation:** Postpone or rethink typography changes unless further evidence supports it.

---

### 🛠️ Tools Used
- Python (pandas, matplotlib, seaborn, scipy, statsmodels)
- Jupyter Notebook
- Inferential statistics: proportion tests, Bonferroni correction

---

### 📈 Impact of the Analysis
- Prevented a design change with no user benefit.
- Identified conversion bottlenecks in the shopping experience.
- Informed product and UX decisions based on solid data.








