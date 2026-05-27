# Guía del Mentor: Sesión 2 - IA Generativa & Arquitectura RAG
## Mentoría de Posicionamiento IT / AI para Claudio Vernuccio

---

## 🎯 Objetivo de la Sesión
Capacitar al mentorado para hablar con propiedad matemática y arquitectónica sobre Inteligencia Artificial Generativa. Al finalizar esta sesión de 60 minutos, Claudio comprenderá físicamente cómo se procesa la información corporativa, los límites económicos del software probabilístico, y sabrá estructurar un **PRD de IA** consistente para presentarlo como un activo de portafolio comercial en entrevistas internacionales.

---

## ⏱️ Agenda de la Sesión (60 Minutos)

| Minutos | Módulo | Diapositivas | Foco Pedagógico |
| :--- | :--- | :--- | :--- |
| **00 - 05 min** | Introducción e Ideación | Slide 1 | El cambio mental de PM tradicional a PM de IA. |
| **05 - 15 min** | Desmitificación y Límites Físicos | Slides 2 - 4 | Next-Token, Tokens, Caching, Context Windows y "Lost in the Middle". |
| **15 - 30 min** | Los Bloques de RAG | Slides 5 - 7 | Embeddings, Vectores, Metadata Filtering y Chunking con Overlap. |
| **30 - 45 min** | Taller Práctico RAG | Slides 8 - 10 | Simulación del Cargill Customs Bot y la anatomía del PRD. |
| **45 - 55 min** | Gobernanza, Alucinaciones y QA | Slides 11 - 13 | Enterprise SLAs, Thresholds, Golden Datasets y Observabilidad (Evals). |
| **55 - 60 min** | Roleplay y Cierre | Slides 14 - 15 | Preguntas estrella de entrevistas IT y entrega de consigna de portafolio. |

---

## 🤖 Co-Mentoring Técnico con NotebookLM

> [!TIP]
> Antes de la sesión, pídele a Claudio que suba la guía completa de la mentoría y el manual técnico de la arquitectura a **NotebookLM**. Utilicen el siguiente prompt exacto para simular un copiloto de consultas durante la clase:

```text
Actúa como un CTO y Arquitecto Principal de Inteligencia Artificial de Cargill. 
Tu objetivo es auditar técnicamente mis propuestas para el "Cargill Customs Bot" (asistente RAG). 
Cuando te haga una pregunta sobre la implementación de tokens, embeddings o límites de contexto, 
respóndeme en un tono profesional, pragmático y exigente, contrastando mi rol de Product Manager con la viabilidad real del software.
```

---

## 🖋️ Metáforas Visuales para la Pizarra Concepto

Para facilitar el entendimiento conceptual sin abrumar con código matemático, dibuja las siguientes analogías en la pizarra en tiempo real:

### 1. El escritorio del LLM (Ventana de Contexto & Lost in the Middle)
```text
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│  [ RESOLUCIONES ]       [ lost in the middle ]       [ TARIFAS ] │
│  Retención: 99%          Retención: ~40%             Retención: 99%
│  (Zona Caliente)         (ZONA FRÍA / RUIDO)         (Zona Caliente)
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### 2. El Balance de Chunking & Overlap
```text
Documento Completo:
[... puerto de San Lorenzo requiere habilitación de aduana fluvial de carga ...]

Fragmento A (Chunk Size: 50):   [... puerto de San Lorenzo requiere habilitación de aduana ]
                                                                 /\
                                                                /  \ (Overlap 15%)
                                                               \    /
Fragmento B (Chunk Size: 50):                                  [ aduana fluvial de carga ...]
```

---

## 🎙️ Guion Verbatim Diapositiva por Diapositiva

### 🛝 Slide 1: Portada (Ideación & Propuestas de Valor con IA)
*   **Guion**: *"Claudio, bienvenido a la Sesión 2. En nuestro primer encuentro consolidamos las bases del software clásico, APIs, Git y DevOps. Hoy daremos el salto más esperado en el mercado actual: entenderemos cómo actúa la Inteligencia Artificial Generativa desde adentro. Diseñaremos tu primer producto de IA de alta fidelidad, al que llamaremos 'Cargill Customs Bot', y aprenderemos a estructurar un documento de requerimientos (PRD) sólido que demuestre a cualquier director de tecnología que comprendés la viabilidad económica y técnica de la IA empresarial."*

### 🛝 Slide 2: Desmitificando los LLMs (Del Hype a la Probabilidad)
*   **Guion**: *"El primer error del PM no técnico es antropomorfizar la Inteligencia Artificial. Un LLM no razona, no comprende conceptualmente como un ser humano, y no tiene conciencia. Científicamente, es un motor probabilístico estadístico de predicción de la siguiente sub-palabra más probable. Cuando le hacemos una consulta, calcula la probabilidad matemática de cada palabra siguiente basándose en su entrenamiento. Comprender que consumimos un servicio de API matemático nos permite estructurar defensas de seguridad y eliminar el mito del 'cerebro mágico' en las reuniones ejecutivas."*

### 🛝 Slide 3: La Economía de la IA: Arquitectura de Tokens (Input vs. Output)
*   **Guion**: *"Toda solución con IA tiene costos variables críticos. Los LLMs no leen texto crudo, leen 'tokens', que son sub-palabras o bloques lógicos. En promedio, 1000 tokens equivalen a 750 palabras. Las APIs comerciales cobran por volumen de tokens procesados y la tarifa es asimétrica: el costo de los tokens que le inyectamos al modelo en el prompt es considerablemente más barato que el costo de los tokens que el modelo tiene que generar en su respuesta. Para optimizar esto a gran escala, implementamos 'Prompt Caching', una técnica que almacena en memoria los bloques de instrucciones fijos para evitar volver a facturarlos en llamadas sucesivas."*

### 🛝 Slide 4: Ventanas de Contexto & El Fenómeno "Lost in the Middle"
*   **Guion**: *"La ventana de contexto representa el escritorio físico temporal del modelo. Aunque modelos modernos admiten millones de tokens, los LLMs sufren un sesgo denominado 'Lost in the Middle'. Tienden a recordar y analizar con precisión quirúrgica de hasta el 99% la información que se ubica al principio y al final del prompt, pero su tasa de retención se desploma drásticamente, llegando hasta el 40%, para los datos ubicados en el centro geométrico del contexto. Como PM, tu rol no es tirarle PDFs enteros al modelo, sino inyectar exactamente el dato preciso que el usuario necesita."*

### 🛝 Slide 5: Embeddings: Traduciendo Lenguaje Natural a Coordenadas
*   **Guion**: *"¿Cómo logra la máquina procesar semánticamente que 'Puerto de Rosario' y 'Terminal Fluvial' están asociados si no comparten una sola palabra? Mediante Embeddings. Un modelo de embeddings toma un texto y lo convierte en un vector de alta dimensión (típicamente de 1536 dimensiones). En este espacio tridimensional conceptual, los conceptos con afinidad de negocio se ubican geométricamente muy cerca de sí mismos, permitiendo búsquedas conceptuales que el software clásico de búsqueda por palabras clave jamás podría resolver."*

### 🛝 Slide 6: Bases de Datos Vectoriales & Metadata Filtering
*   **Guion**: *"Una vez generados los vectores de nuestros documentos empresariales, debemos almacenarlos en bases de datos vectoriales como Pinecone o Chroma. Sin embargo, realizar una búsqueda semántica pura en millones de vectores puede recuperar datos antiguos o de otros puertos. Para solucionar esto, implementamos 'Metadata Filtering' en nuestro PRD: antes de buscar semánticamente similitud en la base vectorial, aplicamos un filtro duro estructurado de metadatos (como Puerto, Año o Regulador), restringiendo la búsqueda del bot únicamente al cuadrante relevante."*

### 🛝 Slide 7: Chunking: Estrategias de Fragmentación Documental
*   **Guion**: *"Para que los manuales portuarios entren en la ventana de contexto, debemos cortarlos en pedazos pequeños llamados 'Chunks'. Pero si hacemos un corte rígido de caracteres, podemos cortar a la mitad una resolución arancelaria, destruyendo su significado. La solución es configurar 'Overlap' o solapamiento semántico, repitiendo típicamente entre un 10% y un 20% del texto del final del fragmento A al inicio del fragmento B. Calibrar la relación de fragmentación y solapamiento es una de las tareas técnicas más importantes del PM de IA."*

### 🛝 Slide 8: Anatomía de RAG: Fase 1 - Ingestión del Dato Privado
*   **Guion**: *"La arquitectura estrella para integrar datos privados de negocio sin incurrir en entrenamientos multimillonarios de modelos se llama RAG: Retrieval-Augmented Generation. Su primera fase es la Ingestión (offline o batch). En esta etapa, tomamos todos los manuales de logística y aduanas de Cargill, aplicamos estrategias de chunking con overlap, los pasamos por un modelo de embeddings y almacenamos los vectores resultantes de forma segura en Pinecone. Con esto, preparamos la base de conocimiento estructurado."*

### 🛝 Slide 9: Anatomía de RAG: Fase 2 - Consulta del Usuario en Tiempo Real
*   **Guion**: *"La fase 2 de RAG ocurre en vivo (live) cuando el usuario pregunta algo. El sistema convierte la pregunta del analista en vector, busca los fragmentos semánticamente más similares en Pinecone, y genera un prompt enriquecido: 'Responde a la siguiente consulta basándote estrictamente en este contexto verificado'. El LLM analiza este fragmento y genera una respuesta 100% verídica basada en los manuales inyectados. Es una arquitectura de libro abierto altamente confiable."*

### 🛝 Slide 10: Taller: El Mock PRD del "Cargill Customs Bot"
*   **Guion**: *"Llevemos la teoría a la práctica técnica. Diseñaremos el Mock PRD de nuestro 'Cargill Customs Bot', un producto orientado a asistir a despachantes de soja y maíz para auditar regulaciones fluviales. En este taller especificaremos qué fuentes documentales indexaremos, determinaremos la latencia de respuesta aceptable del bot y definiremos las reglas técnicas para el equipo de desarrollo. Este entregable será el primer gran activo técnico de tu portafolio en LinkedIn."*

### 🛝 Slide 11: Gobernanza de IA, Privacidad & Fuga de Datos (Leakage)
*   **Guion**: *"Como Product Manager Sénior, la seguridad de la información corporativa es tu máxima prioridad. Nunca debemos permitir que los empleados expongan datos confidenciales (tarifas de fletes, identidades de despachantes) a modelos públicos sin contratos de privacidad. En tu PRD debes exigir el uso de APIs corporativas bajo acuerdos de Enterprise SLAs. Estos acuerdos garantizan cifrado absoluto y, fundamentalmente, que los datos inyectados jamás se retengan ni se utilicen para re-entrenar modelos públicos comerciales."*

### 🛝 Slide 12: Mitigación de Alucinaciones: Umbrales y Lógica "No-Answer"
*   **Guion**: *"Las alucinaciones en un entorno industrial como Cargill pueden costar millones de dólares en multas portuarias. Para mitigar esto, implementamos 'Confidence Thresholds'. Cada fragmento que recupera la base vectorial tiene un score de similitud semántica. Si el score es inferior al umbral que calibraremos (ej. 0.75), bloqueamos el envío al LLM y programamos al bot para responder con seguridad: 'No dispongo de registros oficiales para responder a tu consulta'. Esto evita respuestas inventadas por completo."*

### 🛝 Slide 13: Evaluación de Calidad: Golden Dataset y Observabilidad (Evals)
*   **Guion**: *"En la IA clásica no podemos evaluar el software interactuando a mano 5 minutos; necesitamos auditorías estadísticas. Por ende, estructuraremos un 'Golden Dataset': un banco de 50 preguntas y respuestas perfectas validadas por expertos de aduanas. Ante cada cambio de prompt o base de datos, ejecutaremos este benchmark de forma automatizada en el pipeline de desarrollo usando herramientas de observabilidad como Langfuse, garantizando que el producto no sufra regresiones de precisión semántica."*

### 🛝 Slide 14: Roleplay: Defensa Técnica de IA en Entrevistas de Trabajo
*   **Guion**: *"Simulemos una entrevista de alto impacto. Si un CTO te pregunta cómo resolverías de forma económica la desactualización de datos y alucinaciones de nuestro bot, tu respuesta no debe ser realizar Fine-Tuning, ya que el fine-tuning es para estilo y tono. Tu propuesta debe ser estructurar un pipeline RAG con Metadata Filtering para restringir las búsquedas vectoriales a fragmentos específicos de la base de datos de aduanas. Esta defensa demuestra seniority estratégico absoluto."*

### 🛝 Slide 15: Tu Ruta y Valor como IT Product/Project Manager
*   **Guion**: *"Para cerrar esta gran sesión, Claudio, consolidemos por qué este conocimiento técnico te diferencia de un PM genérico. En tus entrevistas y en tu día a día, entender tokens te capacita para estimar y defender presupuestos de APIs de IA para evitar desvíos financieros en la corporación; comprender RAG y overlap te permite fijar criterios de aceptación (DoD) sólidos para tu equipo de ingenieros; y dominar Enterprise SLAs te permite liderar la gobernanza de datos y evitar filtraciones críticas de secretos comerciales. Diferenciemos esto en tu roadmap hacia el mercado: hoy en la Sesión 2 dominaste la 'IA Pasiva' mediante RAG y bases vectoriales para recuperar conocimiento interno. En la Sesión 3 avanzaremos hacia la 'IA Activa' con Sistemas Agénticos Autónomos que llaman a APIs externas y toman decisiones de flujo. Y en la Sesión 4 cerraremos con 'IA a Escala', implementando observabilidad, pipelines de Evals automatizadas en CI/CD y despliegue robusto en la nube. ¡Excelente semana, completa la plantilla del Mock PRD y nos vemos en la Sesión 3!"*

