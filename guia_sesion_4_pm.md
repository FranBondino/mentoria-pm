# Guía del Mentor: Sesión 4 — Simulación de Entrevista & Evals (Cierre)
## Mentoría de Posicionamiento IT / AI para Claudio Vernuccio

---

## 🎯 Objetivo de la Sesión
Esta sesión es de **cierre, consolidación y práctica intensiva**. El objetivo no es introducir nuevos conceptos teóricos, sino capacitar a Claudio para defender con absoluta solidez técnica toda la arquitectura estudiada en las semanas previas (APIs, Git, RAG y Agentes Autónomos). Al finalizar estos 60 minutos, Claudio habrá resuelto incidentes de producción, construido un *Golden Dataset*, calibrado métricas de evaluación estadística (*Evals*) y superado un simulacro de auditoría técnica (*CTO Audit*).

---

## ⏱️ Agenda de la Sesión (60 Minutos)

| Minutos | Módulo | Diapositivas | Foco Pedagógico & Ejercicios |
| :--- | :--- | :--- | :--- |
| **00 - 05 min** | Check-in y Reglas | Slide 1 | **Alineación del "Muro de Fuego"**: Repaso del estado emocional de Claudio, desbloqueo de dudas y definición del marco de alta exigencia para el simulacro. |
| **05 - 25 min** | Módulo 1: Calidad & Evals | Slides 2 - 5 | **Taller de Calidad de Datos**: Introducción teórica al *Golden Dataset*, construcción en vivo de filas con *Ground Truth* y calibración de métricas de *Faithfulness*, *Answer Relevance* y *Recall*. |
| **25 - 40 min** | Módulo 2: Incidentes | Slide 6 | **Resolución de Crisis en Vivo**: Resolver logs reales de producción. Diagnóstico de loops agénticos, fallos de APIs aduaneras y mitigación de alucinaciones. |
| **40 - 55 min** | Módulo 3: CTO Audit | Slides 7 - 9 | **Simulacro de Auditoría (Roleplay)**: Responder a preguntas trampa de un CTO internacional sobre Fine-tuning vs RAG, ciberseguridad, SLAs, modularidad de agentes y latencias. |
| **55 - 60 min** | Cierre y DoD | Slides 10 - 11 | **DoD del Programa & Optimización de CV**: Validación final del cumplimiento de objetivos (*Definition of Done*) y optimización de CV/LinkedIn para el rol de supervisión. |

---

## 🗺️ Diferencia de Alcance: Sesión 2 vs. Sesión 3 vs. Sesión 4
Esta tabla resume la progresión de Claudio, ayudándolo a estructurar su speech final ante directores de tecnología:

| Eje de Comparación | Sesión 2: IA Pasiva & RAG | Sesión 3: IA Activa & Agentes | Sesión 4: Consolidación & Simulación (Hoy) |
| :--- | :--- | :--- | :--- |
| **Foco Pedagógico** | Recuperación e inyección de datos de dominio de forma estática en prompts. | Sistemas que ejecutan acciones, toman decisiones y llaman a APIs externas de forma autónoma. | **Práctica real y entrevistas**: Resolución de crisis, datasets de evaluación y simulacro de contratación. |
| **Arquitectura Clave** | RAG (Chunking + Embeddings + Vector Database). | Loops de razonamiento (ReAct) + Orquestadores + Tool Calling. | Pipelines de monitoreo continuo (Langfuse) + Evals automatizadas en CI/CD. |
| **Dinámica del Bot** | **De Libro Abierto**: El LLM lee el material y resume. No altera el mundo externo. | **Ejecutor Autónomo**: El bot modifica bases de datos, envía correos y llama a APIs internas. | **Auditor y Guardián**: Herramientas que controlan latencia, costos y previenen alucinaciones. |
| **Actividad Práctica** | Mock PRD del "Retail Support Bot". | PRD y Diagrama de Flujo del Agente de CRM y despachos. | **Golden Dataset & Tablero de Evals**: Definición de pruebas fácticas y métricas de producción. |

---

## 🤖 Co-Mentoring con NotebookLM
> [!TIP]
> Antes de iniciar la clase, pídele a Claudio que cargue las guías anteriores y esta misma guía en **NotebookLM**. Utilicen el siguiente prompt para simular dudas y respuestas rápidas durante la clase:
> ```text
> Actúa como un CTO internacional exigente. Tu objetivo es auditar técnicamente mis respuestas durante el simulacro de entrevista de la Sesión 4. Evalúa mi rigor metodológico (doctrina de software, Git, APIs, gobernanza de IA) y califica mis respuestas del 1 al 10, dándome feedback de mejora inmediata.
> ```

---

## 💬 Módulo 0: Check-in y Rompehielos (00 - 05 min)
* **Objetivo Metodológico**: Reducir la ansiedad de Claudio ante la idea de una "entrevista técnica", validar que haya repasado los conceptos clave de RAG y Agentes, y setear las reglas de juego (el mentor será un evaluador estricto pero constructivo).
* **Guion del Mentor (Break the Ice)**:
  > *"Hola Claudio, ¿cómo estás? Llegamos a la sesión 4. Hoy completamos el ciclo de mentoría. En las sesiones previas construimos las bases de software: Git, entornos, APIs, RAG y flujos agénticos. Hoy no vamos a sumar nada de teoría nueva. Toda tu energía hoy está enfocada en la práctica, la simulación y el speech. Hoy tu rol es defender todo lo que diseñaste como un Senior Technical Project Manager de IA ante directores de tecnología globales. Antes de arrancar con los incidentes, cuéntame: ¿cómo te sientes con el material de las sesiones anteriores y qué dudas te quedaron flotando durante la semana?"*
* **Posibles desvíos de Claudio**:
  - *Si Claudio dice que está inseguro con la programación en Python*: Recuérdale que su valor en el mercado no es escribir código de memoria, sino entender la lógica de la arquitectura para liderar a los ingenieros y auditar la calidad.
  - *Si Claudio tiene dudas puntuales de RAG*: Prométele que las resolverán en vivo al calibrar las métricas en la Slide 4.
* **Guion de Transición**:
  > *"Excelente, Claudio. La dinámica de hoy se llama 'Muro de Fuego'. Los próximos 60 minutos simularán el ritmo de una auditoría real de QA. Vamos a pasar a la Diapositiva 1 para ver el mapa general."*

---

## 📝 Guiones Detallados de las Diapositivas & Ejercicios

### 🛝 Slide 1: Portada (Simulación de Entrevista & Evals)
* **Objetivo Metodológico**: Romper el hielo, setear el tono de alta exigencia de la sesión y felicitar al alumno por su constancia en el estudio.
* **Guion del Mentor**: 
  > *"Claudio, bienvenido formalmente a la sesión 4. Como ves en pantalla, el título de hoy es Simulación de Entrevista y Evals. Tu valor diferencial en el mercado internacional radica en tu capacidad para unir tus 10 años de experiencia operativa en Retail Enterprise con la arquitectura técnica moderna de IA. En esta sesión asumiremos que eres el PM técnico a cargo del Retail AI Agent. Lideraremos la resolución de incidentes en caliente, diseñaremos un Golden Dataset interactivo para medir calidad, y defenderemos el sistema ante un CTO que nos auditará costes, latencias y seguridad legal. Pasemos a la diapositiva 2 para ver el cronograma exacto."*
* **⚡ Dinámica Interactiva**: Pregúntale a Claudio si comprende el alcance de las responsabilidades de un PM técnico de IA comparado con un PM tradicional de metodologías ágiles.
* **🔗 Transición**: *"Vamos a la Slide 2 para analizar los tres bloques de nuestro Muro de Fuego de 60 minutos."*

---

### 🛝 Slide 2: Estructura del "Muro de Fuego" (Cronograma)
* **Objetivo Metodológico**: Explicar la dinámica de la sesión, asegurando que Claudio comprenda el ritmo y la distribución del tiempo para manejar la presión.
* **Guion del Mentor**:
  > *"Esta sesión está estructurada como un ciclo de auditoría de ciberseguridad y QA en una multinacional. Dedicaremos los primeros 15 minutos a resolver incidentes críticos de producción a nivel de infraestructura. Luego, pasaremos a un bloque de 20 minutos de control estadístico de calidad de IA, construyendo un Golden Dataset en vivo y analizando métricas matemáticas. Finalmente, tendremos 20 minutos de simulacro de entrevista técnica, el CTO Audit, donde me pondré en la piel de un CTO muy desconfiado de la IA que te interrogará sobre costos y seguridad. Empecemos de inmediato con la Slide 3 para armar nuestra base de pruebas."*
* **⚡ Dinámica Interactiva**: Haz que Claudio lea los títulos de los bloques y valide que está listo para iniciar el primer bloque práctico de Incidentes.
* **🔗 Transición**: *"Pasamos a la Slide 3 para iniciar con el Taller de Calidad de Datos."*

---

### 🛝 Slide 3: Concepto — El Golden Dataset y la Inferencia
* **Objetivo Metodológico**: Explicar la diferencia entre probar software tradicional (determinista) y software probabilístico (LLM), introduciendo el rol clave del *Golden Dataset* y el *Ground Truth*.
* **Guion del Mentor**:
  > *"Claudio, antes de hacer el ejercicio práctico, es fundamental entender un concepto de QA. En el desarrollo de software tradicional, si ponés un input, siempre tenés el mismo output. Pero con modelos de lenguaje, el output es probabilístico. No sirve de nada probar 'chateando' de forma improvisada. Para auditar la calidad, construimos un **Golden Dataset**: una base de datos con consultas típicas de los usuarios y las respuestas perfectas redactadas por expertos, conocidas como **Ground Truth**. Al subir cambios al código o a los prompts, el sistema corre automáticamente estas preguntas en el pipeline de CI/CD para calcular su precisión antes del despliegue. Analicemos cómo se compone esta estructura."*
* **⚡ Dinámica Interactiva**: Preguntale a Claudio si en su experiencia en Retail Enterprise tenían bases de datos de prueba similares para validar flujos aduaneros o ERP, y hacé hincapié en que el *Ground Truth* siempre debe ser redactado por humanos expertos de negocio, nunca autogenerado por otra IA para evitar sesgos.
* **🔗 Transición**: *"Ahora que entendemos el concepto de Golden Dataset, pasemos a la Slide 4 para construir uno en vivo."*

---

### 🛝 Slide 4: Ejercicio — Creación de un Golden Dataset en Vivo
* **Objetivo Metodológico**: Hacer que Claudio elija y justifique la redacción de consultas de usuario, respuestas de referencia (*Ground Truth*) y fragmentos del manual para armar la base de testeo del Retail Support Bot.
* **⚡ Dinámica Interactiva (Paso a Paso)**:
  El mentor va agregando cada una de las 3 filas del Golden Dataset usando los botones del widget interactivo de las slides. Para cada fila agregada, realiza una pregunta específica para que Claudio justifique el diseño del caso de prueba:
  1. **Fila 1 (Políticas de Reembolso)**:
     - **Pregunta del Mentor**: *"Claudio, si comparamos la pregunta 1 ('¿Puedo devolver un suéter comprado en liquidación hace 15 días?') con la respuesta del manual y el Ground Truth, vemos que el manual menciona 'liquidación especial' y 'cupones de crédito de tienda' pero el Ground Truth especifica 'liquidación de temporada' y 'crédito de tienda'. ¿Por qué es crucial alinear la terminología exacta y evitar ambigüedades al redactar el Ground Truth?"*
     - **Respuesta esperada de Claudio**: Para que la evaluación semántica automatizada funcione, el Ground Truth debe usar la terminología de dominio exacta del manual indexado. Si el Ground Truth emplea términos diferentes o vagos, la métrica de *Context Recall* o *Answer Relevance* daría un falso negativo al comparar la respuesta del bot (basada en el manual) con un Ground Truth redactado con términos sinónimos pero no idénticos.
  2. **Fila 2 (Costos de Envío)**:
     - **Pregunta del Mentor**: *"Si el manual indica un límite de envío gratis a partir de $50.000 ARS y un plazo de entrega de 2 a 4 días hábiles, y el bot le responde al usuario que el envío es gratuito para cualquier monto y que llega en 24 horas, ¿cuál es el riesgo y cómo calificaría la fidelidad (Faithfulness) de esa respuesta?"*
     - **Respuesta esperada de Claudio**: El riesgo es financiero (pérdida de margen por envíos gratuitos no estipulados) y reputacional (quejas por promesas de entrega incumplidas). La fidelidad (Faithfulness) se calificaría con 0 o muy bajo porque contradice directamente la verdad provista en el manual. Esto demuestra que en sistemas probabilísticos, un desvío mínimo en valores críticos arruina la fidelidad del bot.
  3. **Fila 3 (Cobro Duplicado)**:
     - **Pregunta del Mentor**: *"Si se detecta un reclamo por cobro duplicado, el bot debe pausar el pedido e iniciar un reporte en la pasarela de pagos. ¿Por qué esto se define como una compuerta determinista estricta en el API Gateway y no se deja al criterio del LLM decidir si pausa o no la orden?"*
     - **Respuesta esperada de Claudio**: Porque los LLMs son probabilísticos y no garantizan el cumplimiento de protocolos de seguridad y prevención de fraude. Un cobro duplicado requiere suspender la transacción y escalar a revisión del área de finanzas (HITL) de inmediato; esa lógica transaccional debe ser una regla dura programada en el backend/middleware, previniendo fallas y pérdidas económicas.
  4. **Pregunta Conceptual de Cierre**: *"Si un desarrollador del equipo te propone poblar el Ground Truth de forma automatizada usando GPT-4 para ahorrar tiempo, ¿qué le responderías y por qué es un riesgo de negocio?"*
     - **Respuesta esperada de Claudio**: Le respondería que no es viable. Utilizar un modelo generador probabilístico (como GPT-4) para redactar el Ground Truth introduce un sesgo de alineación del propio modelo y valida posibles alucinaciones silenciosas. El Ground Truth representa la "verdad de negocio" absoluta y debe ser redactado por expertos de dominio humanos para auditar de forma independiente a la IA.
* **Guion del Mentor**:
  > *"Claudio, las aplicaciones de IA no se pueden probar chateando de forma improvisada antes de producción. Implementamos un Golden Dataset. Como ves en el constructor interactivo de la diapositiva, agreguemos casos de prueba. Observa la relación entre la pregunta del usuario, el contexto oficial extraído y la respuesta experta (Ground Truth). Vamos a analizar la lógica detrás de cada fila que agregamos y a justificar por qué estructuramos así los casos de prueba."*
* **🔗 Transición**: *"Ahora que entendemos cómo estructurar un dataset de control, pasemos a la Slide 4 para ver cómo evaluamos matemáticamente si las respuestas del bot se alinean con este dataset."*

### 🛝 Slide 5: Ejercicio — Calibración del Tablero de Evals
* **Objetivo Metodológico**: Analizar las tres métricas fundamentales de evaluación probabilística (*Faithfulness*, *Answer Relevance* y *Context Recall*) y calibrar sus umbrales óptimos para producción.
* **⚡ Dinámica Interactiva (Paso a Paso)**:
  El mentor y Claudio alternan entre las métricas en la diapositiva para examinar las fórmulas en el panel derecho. El mentor evalúa a Claudio en cada métrica con un escenario de falla real:
  1. **Faithfulness (Fidelidad)**:
     - **Pregunta del Mentor**: *"Claudio, supongamos que el bot responde: 'Las prendas en liquidación no admiten reembolsos en efectivo, y además te comento que los nuevos suéteres de cachemira de temporada son hermosos'. Si el manual de ventas no menciona en absoluto la belleza de la nueva colección, ¿cómo se ve afectada la fidelidad en Evals?"*
     - **Respuesta esperada de Claudio**: La fidelidad (Faithfulness) baja porque una parte de la respuesta no se puede verificar a partir del contexto recuperado. La métrica calcula (Sentencias Verificables en Contexto / Total de Sentencias Generadas); agregar información irrelevante o inventada en la respuesta, aunque sea inofensiva, penaliza el score e indica alucinación.
  2. **Answer Relevance (Relevancia)**:
     - **Pregunta del Mentor**: *"Si el usuario pregunta: '¿Cuáles son las sucursales físicas habilitadas para cambios?' y el bot responde: 'Nuestra marca tiene locales en todo el país. Vendemos prendas de alta calidad y calzado moderno...'. ¿Por qué esta respuesta tiene una relevancia muy baja, si es que no alucina nada?"*
     - **Respuesta esperada de Claudio**: Porque es una respuesta evasiva que no contesta la pregunta del usuario. Answer Relevance mide la alineación semántica de la respuesta con la consulta; irse por las ramas o dar rodeos conceptuales sin enumerar las sucursales habilitadas para cambios penaliza severamente el score.
  3. **Context Recall (Recuperación - Alerta Roja 0.40)**:
     - **Pregunta del Mentor**: *"Supongamos que el dashboard de Langfuse nos indica que Context Recall cayó a un alarmante 0.40. Si el equipo técnico te propone solucionar esto reescribiendo el System Prompt, ¿qué les dirías? ¿El problema está en el LLM o en la base vectorial (Retrieval)?"*
     - **Respuesta esperada de Claudio**: El problema está en el recuperador (Retrieval) de la Vector DB, no en el LLM. Un recall de 0.40 significa que el sistema sólo recuperó el 40% del manual necesario para contestar la pregunta del experto. Cambiar el prompt no servirá de nada porque la información no llegó a la ventana de contexto. Debemos optimizar el chunking, overlap o revisar metadatos en la indexación.
* **Guion del Mentor**:
  > *"Analicemos las métricas automáticas de auditoría en la diapositiva. Veremos qué pasa cuando las métricas cuantitativas no coinciden con la apariencia superficial de la conversación. Claudio, examina el panel de Evals y decime cómo interpretarías los scores del dashboard en un escenario de producción real."*
* **🔗 Transición**: *"Con el tablero de métricas calibrado, pasemos a la Slide 5 para enfrentar incidentes reales en caliente en producción."*

---

### 🛝 Slide 6: Ejercicio — Resolución de Incidentes en Vivo
* **Objetivo Metodológico**: Simular incidentes comunes de producción y evaluar la capacidad del PM para proponer soluciones lógicas de arquitectura sin necesidad de escribir código.
* **⚡ Dinámica Interactiva (Paso a Paso)**:
  > [!NOTE]
  > En la interfaz de las diapositivas, las soluciones a cada incidente están ocultas por defecto. Pedile a Claudio que analice la consola y proponga la solución. Solo después de que responda, hacé clic en el botón **"Revelar Solución Correcta"** para contrastar.
  1. Seleccionen la pestaña **1. Loop de Tokens Infinitos (CRÍTICO)**. Pídele a Claudio que lee los logs del panel de consola donde el bot reintenta ante un error 409 hasta consumir $12.50 USD.
  2. Pregúntale a Claudio:
     > *"Como PM técnico de este producto, ¿cuál es la mitigación de arquitectura rígida que debes priorizar de inmediato en el backlog para que esto no destruya el presupuesto de la empresa en un fin de semana?"*
  3. *Respuesta esperada*: Definir un límite rígido de **Max Iterations (máximo 5)** en la orquestación del agente y programar un "circuit breaker" que desvíe el control a un operador humano (compuerta HITL) ante fallos recurrentes del ERP. Hacé clic en **"Revelar Solución Correcta"** para mostrar la confirmación.
  4. Seleccionen la pestaña **2. Caída de API de Aduanas (WARN)**. Pregúntale:
      > *"Si la API del correo o de pagos se cae y el bot arroja un Connection Timeout de 503, ¿cómo se mitiga esto para no interrumpir el flujo de compra y despacho de pedidos?"*
  5. *Respuesta esperada*: Implementar reglas de **Fallback con caché local**. En el PRD especificamos que si la API oficial está caída, el bot consulte una tabla de costos de correo fuera de línea previamente almacenada en caché, mostrando un banner de advertencia al usuario: *'API oficial caída. Tarifas mostradas con base en la última actualización del [Fecha]'.* Hacé clic en **"Revelar Solución Correcta"** para validar.
  6. Seleccionen la pestaña **3. Alerta de Alucinación (ATENCIÓN)**. Pregúntale:
     > *"El validador automático de Langfuse detectó que la fidelidad de una respuesta cayó a 0.55. ¿Cómo evitamos que esa respuesta llegue a los ojos del despachante?"*
  7. *Respuesta esperada*: Implementar una capa intermedia de **Guardrails en tiempo real** (como Llama Guard o NeMo Guardrails) que audite la fidelidad del texto generado antes de renderizarlo en el chat del usuario. Si cae por debajo del umbral mínimo de 0.85, la respuesta se bloquea y se muestra un mensaje predefinido: *'No se pudo verificar la información con el manual oficial. Por favor, consulte al supervisor'.* Hacé clic en **"Revelar Solución Correcta"** para cerrar la sección.
* **🔗 Transición**: *"Has resuelto las tres crisis de producción con excelente criterio técnico. Ahora, Claudio, llegó el momento del desafío mayor: pasamos a la Slide 6 para iniciar formalmente tu CTO Audit."*

---

### 🛝 Slide 7: Simulacro — El CTO Audit
* **Objetivo Metodológico**: Adoptar el rol del CTO exigente para evaluar la firmeza de Claudio, su vocabulario técnico y su capacidad de defensa de la gobernanza de IA.
* **Guion del Mentor (como CTO - Tono inquisitivo y cortante)**:
  > *(Cambio de tono a un tono serio e inquisidor)*: *"Claudio, estuve leyendo tu propuesta para el Retail AI Agent. Los agentes autónomos y los LLMs son famosos por inventar información y tomar de forma errática decisiones en producción. ¿Cómo me garantizas que este bot no llamará a APIs del ERP con datos incorrectos de toneladas, comprometiendo nuestro inventario relacional central?"*
* **⚡ Dinámica Interactiva (Paso a Paso)**:
  El mentor realiza las siguientes preguntas de forma secuencial, exigiendo el uso de conceptos de las Sesiones 1-3. Hacé clic en las tarjetas de la diapositiva 6 para contrastar con la Respuesta Estrella:
  1. **Pregunta 1 (RAG vs Fine-Tuning - Sesión 2)**: *"Nuestra base de datos de stock cambia por minuto y el bot da precios antiguos. ¿Deberíamos re-entrenar o hacer Fine-Tuning al modelo para solucionarlo?"*
     - **Respuesta esperada de Claudio**: No. El Fine-Tuning es para adaptar estilo y formato. Para datos factuales y dinámicos se usa **RAG con filtrado de metadatos** (por ejemplo, restringiendo la búsqueda vectorial al puerto y fecha actual).
  2. **Pregunta 2 (DevOps - Sesión 1)**: *"Los prompts del bot cambian cada sprint. ¿Cómo gestiona tu equipo el control de versiones y el despliegue de prompts sin romper el sistema en producción? ¿Usan ramas de Git?"*
     - **Respuesta esperada de Claudio**: Los prompts se tratan como código. Se guardan en repositorios Git y las modificaciones se realizan en una rama de **feature**, se prueban automáticamente contra el Golden Dataset en nuestro pipeline de **CI/CD (Staging)** y, tras pasar el análisis, se integran a **main** para su despliegue. Alternativamente, usamos Prompt Registries (como Langfuse) para desplegarlos vía API sin necesidad de re-compilar.
  3. **Pregunta 3 (Ambientes - Sesión 1)**: *"Para agilizar las pruebas del bot de IA en el ambiente de Staging, ¿podemos conectar el recuperador RAG directamente a la base de datos vectorial de Producción?"*
     - **Respuesta esperada de Claudio**: No. Esto viola la doctrina de **aislamiento de ambientes** (Dev, Staging, Prod). Staging debe consultar una base vectorial de Staging (con datos anonimizados o sintéticos) para evitar fugas de información, escrituras accidentales en producción o contaminación de métricas de observabilidad reales.
* **🔗 Transición**: *"Bien defendido el aislamiento y versionado. Pero no solo me preocupan los datos internos. Pasemos a la Slide 7 para auditar el cumplimiento legal y la seguridad de datos frente al comité directivo."*

---

### 🛝 Slide 8: Preguntas Trampa — Ciberseguridad & SLAs
* **Objetivo Metodológico**: Evaluar el conocimiento de Claudio sobre la gobernanza de datos a nivel enterprise y regulaciones de cumplimiento (Data Leakage y Chunking).
* **Guion del Mentor (como CTO - Tono preocupado)**:
  > *"Nuestros asesores legales están alarmados. Temen que si los agentes de atención o los clientes inyectan datos de compras privadas, datos de facturación o de tarjetas en el chat, esa información se filtre a la nube pública de OpenAI y la competencia la use para entrenar sus modelos. ¿Cómo aseguramos contractualmente que esto no ocurra? ¿Debemos instalar un modelo local de código abierto para evitar riesgos?"*
* **⚡ Dinámica Interactiva (Paso a Paso)**:
  El mentor realiza las siguientes preguntas sobre ciberseguridad y RAG, haciendo clic en las tarjetas de la diapositiva 7 para contrastar las respuestas:
  1. **Pregunta 1 (Gobernanza & SLAs - Sesión 2/4)**: *"Como PM, ¿cómo garantizás que los datos de compras y tarjetas de clientes de nuestra empresa que se envían al bot no se utilicen para entrenar modelos públicos externos?"*
     - **Respuesta esperada de Claudio**: Exigiendo legal y técnicamente el uso de APIs corporativas bajo acuerdos de **Enterprise SLAs** con políticas contractuales de **Zero-Data Retention** (retención en cero). El proveedor se compromete a encriptar los datos, no guardar historial de consultas y prohibir estrictamente el uso de nuestros inputs para entrenar modelos públicos.
  2. **Pregunta 2 (Data Leakage - Sesión 2)**: *"¿Qué es la fuga de datos (Data Leakage) en una aplicación RAG y cómo la mitiga el equipo?"*
     - **Respuesta esperada de Claudio**: Ocurre cuando RAG extrae chunks de información para los cuales el usuario no tiene permisos (ej. un analista junior consultando salarios de directores). Se mitiga aplicando **Metadata Filtering** según la identidad del usuario en Active Directory: antes de realizar la búsqueda semántica, se inyecta un filtro duro de metadatos (como `department_allow == 'ventas'`), aislando físicamente los registros inaccesibles.
  3. **Pregunta 3 (Chunking & Overlap - Sesión 2)**: *"El bot a veces responde con información cortada a la mitad o no encuentra la relación entre dos párrafos continuos de un manual de políticas de devolución. ¿Qué error de diseño hay en RAG y cómo lo solucionas?"*
     - **Respuesta esperada de Claudio**: Es un problema de **Chunk Size** (tamaño de fragmento) y **Overlap** (solapamiento) inadecuados en el pipeline de ingesta. Si los chunks son muy pequeños o el overlap es de 0%, se corta el contexto semántico entre párrafos continuos. La solución es re-indexar los documentos con un tamaño de chunk mayor (ej. 512 tokens) y un overlap del 10% al 20% (ej. 50-100 tokens) para asegurar que el fin de un bloque se solape con el inicio del siguiente, preservando la continuidad informativa.
* **🔗 Transición**: *"Correcto, Claudio. Cumplimos con los requisitos legales de ciberseguridad y optimización de ingesta. Pasemos a la Slide 8 para resolver los problemas de rendimiento y llamadas a servicios externos en sistemas agénticos."*

---

### 🛝 Slide 9: Preguntas Trampa — Control de Agentes Autónomos
* **Objetivo Metodológico**: Evaluar la capacidad de Claudio para resolver problemas financieros (costos de inferencia) y de rendimiento (latencia), además de integraciones legacy.
* **Guion del Mentor (como CTO - Tono impaciente)**:
  > *"El equipo de operaciones me reporta que el agente tarda más de 10 segundos en responder a un usuario porque debe verificar stock, calado y aduana usando Tool Calling secuencial. Los usuarios de negocio se quejan de la lentitud y el equipo técnico me pide más presupuesto para servidores más grandes. ¿Qué optimizaciones arquitectónicas propones como PM para bajar la latencia y los costos financieros?"*
* **⚡ Dinámica Interactiva (Paso a Paso)**:
  El mentor realiza las siguientes preguntas sobre agentes y APIs heredadas, haciendo clic en las tarjetas de la diapositiva 8 para contrastar las respuestas:
  1. **Pregunta 1 (Sistemas Agénticos - Sesión 3)**: *"Un agente autónomo en producción es probabilístico e impredecible. ¿Cómo controlás el formato de sus salidas para que no rompa las integraciones con nuestro sistema de facturación ERP que es determinista?"*
     - **Respuesta esperada de Claudio**: Desacoplando la inferencia de texto libre del flujo transaccional. Implementamos una capa de validación rígida mediante esquemas de datos (**Pydantic** en Python o JSON Schema) que actúan como un 'filtro de ranura rígido'. Si el LLM retorna una variable fuera de formato o vacía, la capa de validación Pydantic arroja una excepción en milisegundos, bloqueando la llamada e impidiendo que el ERP procese una transacción inestable.
  2. **Pregunta 2 (APIs Legacy SOAP - Sesión 1/3)**: *"Nuestros sistemas de logística más antiguos usan APIs SOAP heredadas (WSDL/XML). ¿Cómo puede el agente de IA, que usualmente trabaja con JSON/REST, interactuar con estos servicios legacy sin reprogramar el ERP?"*
     - **Respuesta esperada de Claudio**: Mediante una capa de abstracción intermedia o **API Gateway / Middleware**. En lugar de exponer el XML/SOAP directamente al agente (lo cual consumiría miles de tokens inútiles procesando esquemas XML complejos), creamos un microservicio intermedio REST/JSON. El agente llama al microservicio en JSON, y el middleware traduce el payload JSON a una consulta SOAP/XML estructurada para el ERP legacy, retornándole al agente solo la respuesta simplificada en JSON.
  3. **Pregunta 3 (Latencia & Optimización - Sesión 3/4)**: *"El agente tiene que llamar a 3 APIs diferentes usando Tool Calling para verificar stock de tienda, costo de envío en API de correo y clima en depósito. La latencia total es de 10 segundos, lo cual es inaceptable. ¿Qué propondrías como PM?"*
     - **Respuesta esperada de Claudio**: Proponer:
       - **Parallel Tool Calling** (ejecutar llamadas de APIs no dependientes en paralelo de forma asíncrona).
       - **Prompt Caching / KV Cache** a nivel de API para no volver a procesar y facturar contextos estáticos (como reglamentos aduaneros).
       - Evaluar si podemos reemplazar un loop agéntico ReAct largo por un **Router de tareas determinista** que derive la consulta directamente al agente trabajador específico.
  4. **Pregunta 4 (Arquitectura Multi-Agente - Sesión 3)**: *"Para procesos complejos (despacho, tarifas de envío, stock), ¿por qué diseñar una arquitectura multi-agente en lugar de un único agente que resuelva todo?"*
     - **Respuesta esperada de Claudio**: Por modularidad, costo de contexto y control de calidad. Un agente monolítico requiere un system prompt gigante y muchas herramientas, lo que eleva la latencia y los costos de tokens, y causa confusión y alucinaciones en el Tool Calling. En su lugar, el patrón Supervisor-Trabajadores divide la complejidad para que cada agente especialista maneje un set acotado de herramientas, lo que facilita el testeo independiente, optimiza el costo y garantiza precisión.
* **🔗 Transición**: *(Sal de personaje)*: *"Claudio, felicitaciones. Has superado el simulacro de CTO Audit defendiendo los puntos críticos con excelente léxico técnico de las Sesiones 1, 2 y 3. Pasemos a la Slide 9 para evaluar el cumplimiento de nuestra meta de graduación."*

---

### 🛝 Slide 10: Criterios de Finalización (DoD de la Mentoría)
* **Objetivo Metodológico**: Consolidar y repasar la lista de competencias validadas a lo largo de las 4 sesiones, certificando que Claudio ha cerrado la brecha tecnológica.
* **Guion del Mentor**:
  > *"Repasemos juntos la Definition of Done de tu mentoría. En estas 4 semanas has logrado objetivos enormes: tu speech de re-entry está completamente actualizado al vocabulario de software moderno (Git, CI/CD, APIs, ambientes), comprendes y defiendes la arquitectura RAG frente a propuestas erróneas de Fine-Tuning, dominas el diseño y la gobernanza de sistemas agénticos con compuertas de seguridad HITL y validadores Pydantic, y entiendes la mecánica estadística para evaluar software probabilístico mediante Golden Datasets y Langfuse. Tu ventaja en el mercado es ser el PM técnico que puede sentarse en una mesa con ingenieros de software y comprender exactamente la lógica del sistema para optimizarlo. Pasemos a la última diapositiva para ajustar los hitos en tu portafolio."*
* **⚡ Dinámica Interactiva**: Pídele a Claudio que elija cuál de estos cuatro pilares siente que ha sido su mayor salto de seniority técnico.
* **🔗 Transición**: *"Vamos a la Slide 10 para cerrar con la optimización de tu portafolio laboral."*

---

### 🛝 Slide 11: Optimización del CV para el Rol de PM Técnico
* **Objetivo Metodológico**: Dar pautas concretas para posicionar a Claudio como un PM Técnico de IA que lidera, comprende y supervisa la arquitectura del producto sin necesidad de implementar el código directamente.
* **Guion del Mentor**:
  > *"Para cerrar, Claudio, hablemos de cómo hacer tangible este salto de seniority. En tu CV y LinkedIn debes posicionarte como 'Senior Technical Project Manager — IT & AI Products' o 'Technical Product Manager | AI Systems Architect'. Tu valor diferencial no es programar el código del bot de IA, sino comprender técnicamente los conceptos para supervisar el equipo de ingeniería. Por ejemplo, en tus logros podés destacar: 'Lideré el diseño técnico y gobernanza del Retail AI Agent, especificando la arquitectura de orquestación multi-agente, compuertas Human-in-the-loop y validación estructurada con Pydantic para mitigar riesgos en ERP', o también: 'Supervisé el diseño y la integración de pipelines de Evals estadísticas automatizadas en GitHub Actions con Langfuse, reduciendo las alucinaciones en consultas de clientes'. Esto le demuestra a cualquier Headhunter internacional que sabes liderar proyectos de IA del mundo real desde un rol de dirección técnica. Ha sido un placer acompañarte en este proceso. ¡Mucho éxito en tu camino!"*
* **⚡ Dinámica de Cierre**: Brindá un espacio para que Claudio exprese sus comentarios finales, felicitalo por su esfuerzo e indicale que las diapositivas y guías quedan en su portafolio para su consulta continua.

---

## 🧠 Machete de Respuestas Estrella para el Mentor
Utiliza este resumen rápido durante el simulacro de roleplay para evaluar las respuestas técnicas de Claudio Vernuccio:

* **¿Fine-Tuning para base de stock dinámica?** $\rightarrow$ **NO**. El Fine-Tuning es para adaptar estilo y formato. Para hechos dinámicos y cambiantes se usa **RAG con filtrado de metadatos** (por ejemplo, restringiendo la búsqueda vectorial al puerto y fecha actual del sistema).
* **¿Control transaccional ante fallos en ERP?** $\rightarrow$ Aislamiento por **API Gateway** determinista + Validación rígida de outputs con **Pydantic** (JSON Schema) + Compuertas **Human-in-the-loop (HITL)** ante desvíos superiores a tolerancias (ej. 10%).
* **¿Privacidad de datos y propiedad intelectual?** $\rightarrow$ Llamadas a través de APIs empresariales protegidas bajo **Enterprise SLAs** con políticas de **Zero-Data Retention** y cifrado TLS/AES-256.
* **¿Versionamiento de Prompts en el Ciclo Agile?** $\rightarrow$ Prompts tratados como código, almacenados en Git, testeados en rama de `feature` en el pipeline de **CI/CD** usando el Golden Dataset, y desplegados tras merge a `main` (o vía Prompt Registries en Langfuse).
* **¿Aislamiento de Entornos de Base Vectorial?** $\rightarrow$ Separación estricta de bases de datos vectoriales para Dev, Staging (datos anonimizados/sintéticos) y Prod, evitando fugas, escrituras no autorizadas y contaminación de métricas de observabilidad.
* **¿Chunk Size y Overlap en RAG?** $\rightarrow$ Si la información sale cortada o desconectada, se re-indexa el contenido en la Vector DB usando un tamaño de chunk mayor (ej. 512 tokens) y un overlap del 10% al 20% (ej. 50-100 tokens).
* **¿Integración con APIs SOAP Legacy (WSDL)?** $\rightarrow$ Se implementa una capa de middleware o **API Gateway** que actúe como traductor: el agente llama al middleware en JSON/REST y el middleware traduce a SOAP/XML, entregando una respuesta JSON simplificada.
* **¿Latencia y Optimización operativa?** $\rightarrow$ **Parallel Tool Calling** (ejecución asíncrona de APIs en paralelo), **Prompt Caching / KV Cache** a nivel de API para contextos estáticos, y uso de **Routers deterministas** para evitar loops ReAct innecesarios.
* **¿Arquitectura Multi-Agente vs Monolítica?** $\rightarrow$ Ventajas de modularidad, menor costo de contexto (tokens), facilidad de testeo independiente y reducción drástica de alucinaciones en el Tool Calling.

---

## 💬 Pautas de Roleplay & Evaluación (Para el Mentor)
Sigue estas pautas para mantener el estándar de la mentoría:
1. **No facilites las respuestas**: Deja silencios incómodos si Claudio no encuentra la palabra correcta. Esto simula la presión de la entrevista técnica.
2. **Corrige el vocabulario de inmediato**: Si dice *"el bot de IA se conecta a la base"*, interrúmpelo con cariño y pídele que diga *"el agente interactúa a través de un API Gateway y valida el esquema con Pydantic"*. El lenguaje técnico es el 50% de la evaluación del Headhunter.
3. **Califica la estructura de speech**: Una respuesta de PM Senior debe seguir la estructura: **Afirmación arquitectónica directa** $\rightarrow$ **Justificación técnica y mitigación** $\rightarrow$ **Criterio de negocio/impacto financiero**.
