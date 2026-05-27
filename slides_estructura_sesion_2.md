# Estructura y Guion de Slides (15 Diapositivas): Sesión 2 - IA Generativa & RAG
## Propuesta Visual, Técnica y Estratégica para la Presentación de Claudio Vernuccio

Este documento detalla la estructura, las descripciones técnicas ampliadas, los recursos visuales y el guion detallado para cada una de las **15 diapositivas** de la Sesión 2.

---

## 🎨 Resumen del Sistema de Diseño (Estilo "Dark Premium")
*   **Fondo Principal**: Azul espacial oscuro (`#090d16`) y Gris grafito (`#0f172a`).
*   **Colores de Acento**:
    *   `#3b82f6` (Azul Cobalto): Para elementos clásicos de software y APIs estructuradas.
    *   `#8b5cf6` (Violeta Neón): Para inteligencia artificial, embeddings y flujos semánticos.
    *   `#10b981` (Verde Esmeralda): Para gobernanza, precisión y mitigación de errores.
    *   `#f97316` (Naranja Radiante): Para tokens, costos, limitaciones físicas y alertas.
*   **Aero-Glows**: Degradados radiales y sombras de caja con desenfoque de 25px para simular interfaces futuristas premium.

---

## 🗺️ Diapositiva por Diapositiva: Estructura, Visuales y Guion

### 🛝 Slide 1: Portada (Ideación & Propuestas de Valor con IA)
*   **Contenido**: Título principal, badge de la sesión y breve descripción de la transición metodológica del PM tradicional hacia la IA.
*   **Recurso Visual**: Gradiente animado lineal que conecta el logo de la mentoría con un nodo cerebral inteligente flotante.
*   **🎙️ Guion**:
> *"Bienvenidos a la Sesión 2. En la primera sesión consolidamos la infraestructura del software moderno. Hoy daremos un paso clave: ingresaremos en el cerebro de los productos contemporáneos con Inteligencia Artificial Generativa. Aprenderemos a diseñar soluciones que resuelvan problemas reales de negocio utilizando datos privados del dominio, y daremos forma a su primer Mock PRD de IA: un asistente de regulaciones y logística internacional al que llamaremos 'Cargill Customs Bot'. Lideremos este viaje desde la perspectiva del Product Management estratégico."*

---

### 🛝 Slide 2: Desmitificando los LLMs (Del Hype a la Probabilidad)
*   **Contenido**: Contraste riguroso entre el mito popular de la "conciencia artificial" y la realidad científica de las APIs probabilísticas. Explicación de *Next-Token Prediction*.
*   **Recurso Visual**: Tabla comparativa con animaciones de opacidad que confronta mitos (rojo) con realidades técnicas (verde).
*   **🎙️ Guion**:
> *"Como Product Managers de IA, nuestro vocabulario debe ser extremadamente preciso. Un LLM no tiene conciencia, no razona como un ser humano y no posee intencionalidad. Científicamente, es un motor estadístico de predicción de la siguiente palabra o 'token' más probable dado un texto previo. Consumimos este motor mediante llamadas de API tradicionales. Entender que es un componente lógico determinista pero probabilístico nos permite estructurar sistemas estables y seguros, eliminando el mito del 'cerebro mágico' en las discusiones de negocio."*

---

### 🛝 Slide 3: La Economía de la IA: Arquitectura de Tokens (Input vs. Output)
*   **Contenido**: Definición detallada de tokens. Diferencia de facturación entre el prompt de entrada (Input Context) y la respuesta generada (Output Generation). Introducción al *Prompt Caching*.
*   **Recurso Visual**: Panel de previsualización interactivo que muestra cómo un párrafo de regulaciones portuarias es segmentado físicamente en sub-palabras de diferentes colores para representar tokens.
*   **🎙️ Guion**:
> *"Toda solución de IA tiene un costo variable que el PM debe modelar. Los LLMs no leen palabras, leen 'tokens' (aproximadamente 1000 tokens equivalen a 750 palabras). Las APIs cobran de forma asimétrica: los tokens de entrada son mucho más baratos que los de salida. Por ende, la clave del éxito financiero de nuestro producto radica en estructurar prompts compactos y en implementar 'Prompt Caching', una técnica que almacena en caché contextos estáticos repetidos en el servidor de la API para reducir la facturación hasta en un 50%."*

---

### 🛝 Slide 4: Ventanas de Contexto & El Fenómeno "Lost in the Middle"
*   **Contenido**: Límites físicos de la memoria de corto plazo de los modelos y el problema de degradación de atención en contextos masivos.
*   **Recurso Visual**: Un mapa de calor de atención de IA (gráfico de curva en U) que muestra visualmente cómo la capacidad de recuperación de la IA es del 99% al principio y al final del prompt, pero cae hasta el 40% en el centro geométrico del contexto.
*   **🎙️ Guion**:
> *"La ventana de contexto es el tamaño del escritorio del LLM: define cuánta información puede procesar en una única llamada de API. Aunque existen ventanas de contexto gigantes de millones de tokens, los modelos sufren un sesgo cognitivo llamado 'Lost in the Middle'. Tienden a recordar con alta precisión la información del principio y del final del prompt, pero omiten o confunden los datos ubicados en el centro geométrico del contexto. Nuestro rol como PMs es definir tuberías que inyecten únicamente el dato preciso para evitar este vacío de atención."*

---

### 🛝 Slide 5: Embeddings: Traduciendo Lenguaje Natural a Coordenadas
*   **Contenido**: Definición matemática conceptual de Embeddings y cómo convierten palabras en vectores de alta dimensión.
*   **Recurso Visual**: Gráfico interactivo tridimensional (Vector Space) con nodos flotantes agrupados por relevancia semántica (granos, puertos, buques, etc.) y un nodo aleatorio distante.
*   **🎙️ Guion**:
> *"¿Cómo entiende la máquina el significado de las palabras? Mediante embeddings. Un embedding es un modelo que transforma texto en una lista de coordenadas matemáticas (vectores, típicamente de 1536 dimensiones). En este espacio tridimensional virtual, las palabras con significados similares quedan ubicadas geométricamente muy cerca una de la otra. Así es como el sistema puede comprender que 'Puerto de Rosario' y 'Terminal Fluvial' están íntimamente asociados, aunque no compartan una sola letra común en su escritura."*

---

### 🛝 Slide 6: Bases de Datos Vectoriales & Metadata Filtering
*   **Contenido**: Almacenamiento de embeddings, indexación semántica y optimización de búsquedas a través de filtrado de metadatos estructurados.
*   **Recurso Visual**: Representación visual de un vector asociado a metadatos clave (ej. `{puerto: 'Rosario', anio: 2026, documento: 'Tarifario'}`) y un simulador de consulta rápida.
*   **🎙️ Guion**:
> *"Los embeddings generados se guardan en bases de datos vectoriales como Pinecone, Chroma o PGVector, que actúan como la biblioteca a largo plazo de nuestra aplicación. Sin embargo, realizar una búsqueda semántica pura en millones de vectores puede traer fragmentos irrelevantes. La solución que implementamos como PMs es el 'Metadata Filtering': antes de buscar similitudes semánticas, pre-filtramos la base de datos por metadatos duros estructurados (como puerto, fecha o categoría de aduana), asegurando que la IA busque únicamente en la sección relevante de la biblioteca corporativa."*

---

### 🛝 Slide 7: Chunking: Estrategias de Fragmentación Documental
*   **Contenido**: Métodos de segmentación de documentos (Fixed-size, Recursive, Semantic) y la importancia estratégica del solapamiento (*Overlap*).
*   **Recurso Visual**: Barra de progreso que ilustra un fragmento de texto dividido en bloques A y B, destacando el solapamiento con un color naranja de transición que representa la repetición de palabras críticas.
*   **🎙️ Guion**:
> *"Para que la información de extensos manuales operativos sea digerible por el LLM, debemos realizar un proceso de 'Chunking' o fragmentación. Cortamos los documentos en pedazos de unas 250 palabras. Si el corte es muy brusco, podemos cortar una cláusula contractual por la mitad, destruyendo su significado. Para evitar esto, configuramos un 'Overlap' o solapamiento del 10% al 20%, repitiendo palabras entre un fragmento y el siguiente. Como PMs, calibraremos este balance: muy poca fragmentación satura el contexto; demasiada destruye el sentido."*

---

### 🛝 Slide 8: Anatomía de RAG: Fase 1 - Ingestión del Dato Privado
*   **Contenido**: El flujo Batch o preparación de la información corporativa offline para su indexación vectorial.
*   **Recurso Visual**: Flujo interactivo paso a paso que conecta Documentos -> Chunking -> Embedding -> Vector DB con nodos animados luminosos.
*   **🎙️ Guion**:
> *"La arquitectura estrella para implementar IA corporativa sin incurrir en entrenamientos caros se llama RAG (Retrieval-Augmented Generation). Su primera fase es la Ingestión del dato privado. En esta etapa offline, tomamos los PDFs de reglamentaciones de aduana y logística de la compañía, los fragmentamos mediante chunking, los vectorizamos usando embeddings y los almacenamos en nuestra base de datos vectorial de forma segura. Con esto, nuestra aplicación ha indexado y estructurado todo el conocimiento privado de la empresa, listo para ser utilizado."*

---

### 🛝 Slide 9: Anatomía de RAG: Fase 2 - Consulta del Usuario en Tiempo Real
*   **Contenido**: La orquestación interactiva en vivo que realiza la aplicación cuando el usuario hace una pregunta.
*   **Recurso Visual**: Flujo de consulta interactivo que muestra la secuencia Pregunta -> Búsqueda Vectorial -> Prompt Enriquecido -> LLM -> Respuesta.
*   **🎙️ Guion**:
> *"La segunda fase de RAG ocurre en tiempo real cuando el usuario realiza una consulta. El sistema convierte la pregunta del usuario en vector de forma instantánea, busca los 3 fragmentos de PDF más relevantes en Pinecone y ensambla un prompt enriquecido: 'Eres un asistente experto. Responde a esta pregunta basándote estrictamente en este contexto verificado'. El LLM procesa esta evidencia dentro de su ventana de contexto y genera una respuesta exacta y libre de alucinaciones. Hemos construido un sistema de libro abierto altamente confiable."*

---

### 🛝 Slide 10: Taller: El Mock PRD del "Cargill Customs Bot"
*   **Contenido**: Estructura del documento de requerimientos prácticos de IA (PRD) enfocado en logística de granos y comercio exterior.
*   **Recurso Visual**: Cuadrantes tipo bento grid que desglosan la visión del producto, fuentes de datos de entrada y métricas de ingeniería (latencia e indexación).
*   **🎙️ Guion**:
> *"Llevemos esto a la práctica. Diseñaremos el Mock PRD de nuestro 'Cargill Customs Bot', un asistente inteligente que audita regulaciones de aduana para despachos de soja y maíz. En este taller en vivo, definiremos las fuentes de datos oficiales (resoluciones de aduanas, normativas fluviales), especificaremos las reglas de chunking del equipo técnico y determinaremos los umbrales de latencia. Este PRD será la pieza central de su portafolio técnico para demostrar capacidad de especificación formal."*

---

### 🛝 Slide 11: Gobernanza de IA, Privacidad & Fuga de Datos (Leakage)
*   **Contenido**: Mitigación de riesgos de seguridad. Enterprise SLAs y políticas de exclusión de re-entrenamiento público de modelos.
*   **Recurso Visual**: Tarjetas ilustrativas que contrastan flujos inseguros de datos con túneles empresariales seguros cifrados.
*   **🎙️ Guion**:
> *"La gobernanza del dato es responsabilidad crítica del Product Manager. Nunca debemos exponer datos confidenciales de la compañía (precios, fletes, contratos de clientes) a través de APIs comerciales públicas generales. Al redactar el PRD, debemos especificar obligatoriamente el uso de APIs corporativas bajo acuerdos de nivel de servicio empresariales (Enterprise SLAs), que garantizan que toda llamada sea cifrada de extremo a extremo y que la información nunca sea retenida ni utilizada para entrenar futuros modelos públicos."*

---

### 🛝 Slide 12: Mitigación de Alucinaciones: Umbrales y Lógica "No-Answer"
*   **Contenido**: Cómo calibrar la confianza semántica para prohibir respuestas inventadas cuando el dato no se encuentra indexado.
*   **Recurso Visual**: Diagrama de flujo de decisión que evalúa el Score de similitud semántica. Si el score es mayor a 0.75, procede al LLM; si es menor, bloquea la consulta y responde con un mensaje seguro.
*   **🎙️ Guion**:
> *"Para que una gran corporación confíe en una IA, las alucinaciones deben estar controladas. ¿Cómo lo logramos? Implementando lógica de umbrales. Cada búsqueda semántica en la base vectorial devuelve un 'Score' o porcentaje de relevancia. Si la consulta del usuario no coincide con ningún fragmento real por encima de un umbral que calibraremos (ej. 75%), programamos al bot para que se abstenga de inventar y responda con seguridad: 'No dispongo de esa información en los registros oficiales'. Esta lógica es fundamental para la seguridad del producto."*

---

### 🛝 Slide 13: Evaluación de Calidad: Golden Dataset y Observabilidad (Evals)
*   **Contenido**: El control de calidad en software probabilístico. Uso del Golden Dataset y monitoreo continuo en producción mediante herramientas de observabilidad.
*   **Recurso Visual**: Panel de control conceptual que muestra métricas de fidelidad semántica al contexto (Context Adherence) y relevancia de respuesta.
*   **🎙️ Guion**:
> *"A diferencia del desarrollo de software tradicional, la IA es probabilística e impredecible. No podemos evaluar si el bot funciona probándolo manualmente chateando 5 minutos. Debemos estructurar un 'Golden Dataset': un conjunto de 50 preguntas difíciles validadas con sus respuestas perfectas redactadas por expertos de aduana. Cada vez que el equipo de desarrollo modifique el prompt o actualice el chunking, correremos este dataset de forma automatizada mediante herramientas de observabilidad como Langfuse, asegurando métricas estadísticas de fidelidad objetivas antes de lanzar a producción."*

---

### 🛝 Slide 14: Roleplay: Preguntas Estrella de Entrevistas de IA
*   **Contenido**: Simulación de entrevistas de alto nivel para PMs sénior. Cómo responder técnicamente frente a reclutadores o directores de tecnología.
*   **Recurso Visual**: Tarjetas interactivas con preguntas desafiantes y las respuestas recomendadas de alto impacto estratégico.
*   **🎙️ Guion**:
> *"Simulemos una entrevista técnica. Imaginen que un CTO les pregunta: '¿Cómo solucionarían los problemas de alucinación e información desactualizada de nuestro asistente comercial sin gastar una fortuna?' Su respuesta inmediata debe descartar el Fine-Tuning para datos fácticos, argumentar el uso de arquitectura RAG y detallar el pre-filtrado por metadatos para optimizar velocidad y costos de tokens. Esta respuesta demuestra de inmediato su capacidad técnica y estratégica."*

---

### 🛝 Slide 15: Tu Ruta y Valor como IT Product/Project Manager
*   **Contenido**: El valor estratégico diferencial del PM en IA (costos, DoD, gobernanza) y la clara diferenciación de alcances del Roadmap (Sesión 2 RAG vs. Sesión 3 Agentes vs. Sesión 4 Escala).
*   **Recurso Visual**: Tarjetas duales interactivas que contrastan los súper-poderes del PM con un desglose tabular de alcances (IA Pasiva vs. IA Activa vs. IA Escala).
*   **🎙️ Guion**:
> *"Para cerrar, Claudio, consolidemos por qué este conocimiento te posiciona en la cima del mercado como IT Product/Project Manager. Comprender tokens te permite estimar y defender presupuestos de APIs para evitar desvíos financieros corporativos; dominar RAG y datasets de prueba te permite fijar criterios de aceptación (DoD) claros para el equipo de desarrollo; y entender Enterprise SLAs te capacita para liderar la gobernanza de datos y mitigar fugas. Difecrenciemos esto claramente en tu roadmap de entrevistas: hoy en la Sesión 2 dominaste la 'IA Pasiva' para recuperar conocimiento privado. En la Sesión 3 pasaremos a la 'IA Activa' con agentes autónomos que ejecutan llamadas a APIs externas. Y en la Sesión 4 consolidaremos el despliegue a producción, observabilidad y optimización avanzada en la nube. ¡Excelente semana y a por la consigna semanal del Mock PRD!"*

