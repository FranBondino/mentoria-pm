# Glosario de Master: Sesión 4 - Finanzas de la IA, Evals & Preparación de Entrevistas

Este documento actúa como la referencia técnica y de negocio definitiva para la **Sesión 4: Finanzas de la IA (Economics), Evals y Simulación de Entrevistas**. Cierra el programa de mentoría consolidando los conceptos financieros, de seguridad, y calidad de software probabilístico necesarios para liderar proyectos corporativos de IA Generativa.

---

## I. Conceptos Fundamentales de AI Economics

### 01. AI Economics & ROI de IA
- **Definición**: La disciplina de negocio encargada de medir, analizar y optimizar la viabilidad financiera, el retorno de inversión (ROI) y los costos de infraestructura (COGS) asociados al despliegue de modelos de inteligencia artificial en producción. A diferencia del software tradicional, donde el costo de servidores escala linealmente con los usuarios de forma económica, el software probabilístico de IA consume recursos de cómputo intensivos por cada token de entrada y salida procesado en la GPU.
- **Enfoque Estratégico PM**: Como PM de IA, tu rol fundamental es defender la rentabilidad de las funcionalidades de IA. Debes justificar el caso de negocio demostrando que el ahorro operativo de tiempo y precisión (ej: automatizar la auditoría de contratos en silos fluviales) supera con creces la factura de API por consumo de tokens.

### 02. Prompt Caching (Caché de Contexto)
- **Definición**: Una optimización de bajo nivel a nivel de infraestructura GPU que permite almacenar temporalmente el estado matemático de los tokens del sistema que no cambian (ej. prompts de sistema extensos, manuales de aduana, o regulaciones de la empresa) en la memoria RAM del servidor de inferencia. Cuando el agente realiza consultas consecutivas, el modelo no vuelve a computar la porción estática, sino que reutiliza el estado guardado en caché.
- **Enfoque Estratégico PM**: Prompt Caching es tu mayor herramienta para reducir costos operativos (hasta un 90% en tokens de entrada recurrentes) y acelerar drásticamente el tiempo de respuesta inicial del bot (Time to First Token - TTFT).

### 03. RAG vs. Fine-Tuning (Análisis de Costos)
- **Definición**: La comparación financiera y operativa entre inyectar información dinámica en tiempo real mediante búsquedas semánticas (RAG) y entrenar pesos adicionales de un modelo base con ejemplos estáticos (Fine-Tuning).
- **Enfoque Estratégico PM**: Fine-tuning es sumamente costoso en cómputo inicial y mantenimiento para mantenerlo actualizado. RAG es óptimo para actualizar información factual del negocio de manera inmediata y económica (simplemente actualizando PDFs en la base de datos vectorial).

---

## II. Calidad, Evals y Observabilidad

### 04. AI Evals (Evaluaciones de Calidad)
- **Definición**: Suites de pruebas especializadas para medir el comportamiento de sistemas probabilísticos donde el resultado final cambia constantemente. A diferencia de los tests unitarios tradicionales (que esperan una salida exacta), las Evals utilizan rúbricas de evaluación cuantitativa (scores de 0 a 1) para evaluar dimensiones críticas como:
  - **Fidelidad (Faithfulness)**: Si el bot inventa información fuera del contexto provisto (alucinación).
  - **Relevancia del Contexto**: Si el recuperador de base vectorial trajo la información de silos correcta.
  - **Relevancia de la Respuesta**: Si responde directamente a la consulta del usuario de aduana.
- **Enfoque Estratégico PM**: El PM debe liderar el diseño de las Evals de negocio. Sin una suite de Evals representativa, cualquier cambio en el software de IA se convierte en un riesgo a ciegas.

### 05. Observabilidad & Tracing (Langfuse)
- **Definición**: El monitoreo continuo de los flujos operacionales de los agentes de IA en producción. Herramientas como **Langfuse** capturan la cadena completa de llamadas a modelos y APIs (Traces), permitiendo medir costos, latencias, latencias de primer token (TTFT) e identificar fallas exactas en el loop de razonamiento del agente.
- **Enfoque Estratégico PM**: Langfuse te proporciona el dashboard estratégico para auditar que el agente cumpla con las reglas del negocio, alertar desvíos de presupuesto, y depurar respuestas incorrectas informadas por los usuarios.

### 06. Data Leakage & Privacidad Corporativa
- **Definición**: La protección y blindaje de la propiedad intelectual de la compañía y los datos privados de los clientes ante llamadas a APIs de modelos de lenguaje externos. Evita que la información secreta compartida se filtre y sea utilizada por proveedores de LLM para entrenar futuros modelos públicos.
- **Enfoque Estratégico PM**: Como PM, debes asegurar que los contratos corporativos de API tengan políticas de exclusión de entrenamiento (Zero Data Retention) y que la arquitectura cuente con filtros de regex y clasificadores que bloqueen información confidencial antes de que abandone el servidor.

---

## III. Ejercicios Prácticos y Simulación de Entrevistas

### Ejercicio 1: Estimación de ROI & Caso de Negocio (Auditoría Fluvial)
**Caso**: Calcular el ahorro operativo mensual al automatizar la auditoría de contratos fluviales con un agente de IA en comparación con una revisión manual humana.

- **Volumen**: 10.000 contratos al mes.
- **Tamaño del Contrato**: ~10.000 tokens promedio de entrada (reglamentos, contratos, prompt).
- **Costo de API (ej. GPT-4o)**: $5 por 1M tokens de entrada, $15 por 1M tokens de salida.
- **Cálculo con Prompt Caching (80% de descuento en la base estática de 8.000 tokens)**:
  - 2.000 tokens de entrada a tarifa normal: $0.01 USD.
  - 8.000 tokens de entrada en caché (con 80% de descuento, es decir, $1.25 por 1M): $0.01 USD.
  - 500 tokens de respuesta generados a tarifa normal ($15 por 1M): $0.0075 USD.
  - **Costo total por contrato**: $0.0275 USD.
  - **Costo mensual total de IA**: $275 USD.
- **Costo de Revisión Manual Humana**: Un analista junior revisa 5 contratos por hora con un costo por hora de $15 USD. Para 10.000 contratos, se requieren 2.000 horas de trabajo mensual (equivalente a ~12 analistas contratados a tiempo completo), costando **$30.000 USD al mes**.
- **Ahorro operativo neto**: **$29.725 USD al mes** (ahorro superior al 99%), reduciendo el tiempo de procesamiento de semanas a segundos.

---

### Ejercicio 2: Suite de Evals de Calidad (LLM-as-a-judge)
**Caso**: Implementar una rúbrica en Langfuse para auditar el desempeño de un agente que responde consultas sobre el estado de granos en los silos.

1. **Rúbrica de Fidelidad (Faithfulness)**:
   - *Instrucción de Evaluación*: Evaluar si la respuesta de la IA contiene hechos que no están respaldados por el contexto provisto por la base de datos de silos.
   - *Score 1.0*: Toda la respuesta se deriva directamente de los datos de silos provistos.
   - *Score 0.5*: Contiene deducciones lógicas razonables, pero no mencionadas en los datos del silo.
   - *Score 0.0*: Menciona toneladas, nombres de barcazas o estados de silos completamente inventados.
2. **Rúbrica de Relevancia del Contexto**:
   - *Instrucción*: Evaluar si los chunks de texto recuperados por la base de datos vectorial son útiles para responder la pregunta del usuario.

---

### Simulación de Entrevistas (Roleplay PM IT/IA)
Preguntas estratégicas clave que plantea un Hiring Manager de tecnología para evaluar la madurez de un PM:

1. **Pregunta sobre Desvío de Presupuesto**:
   - *"Lanzamos el producto al puerto y en una semana nos gastamos todo el presupuesto de API de tokens mensual. ¿Qué pasó y qué hacés?"*
   - *Respuesta PM*: "Audito Langfuse de inmediato para identificar si hay loops infinitos de reintento en el orquestador sin límite máximo de iteraciones, si no estamos aplicando Prompt Caching en las directrices fijas del sistema, o si algún usuario está inyectando inputs masivos sin rate limit. Como solución de corto plazo aplico límites estrictos de reintentos y habilito el caché de contexto".
2. **Pregunta sobre Optimización de Latencia**:
   - *"El cliente del puerto se queja de que el bot tarda 12 segundos en responder. ¿Cómo bajas ese tiempo sin perder precisión?"*
   - *Respuesta PM*: "Primero, implemento streaming de tokens para que el usuario empiece a leer a los milisegundos. Segundo, reduzco la ventana de contexto inyectada optimizando el chunking de los manuales. Tercero, analizo si podemos cambiar el orquestador por un router agéntico directo más liviano para el 80% de las preguntas sencillas".
