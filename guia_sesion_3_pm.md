# Guía del Mentor: Sesión 3 - Flujos Agénticos Avanzados y Casos de Uso Corporativos
## Mentoría de Posicionamiento IT / AI para Claudio Vernuccio

---

## 🎯 Objetivo de la Sesión
Capacitar al mentorado para liderar el diseño de sistemas de **IA Activa** (sistemas agénticos con autonomía). Al finalizar esta sesión de 60 minutos, Claudio comprenderá conceptual y físicamente cómo funcionan los loops de razonamiento cognitivo (ReAct), los patrones de diseño multi-agente (Orchestrator-Workers), la invocación dinámica de APIs mediante Tool Calling, y las compuertas indispensables de gobernanza y control (Human-in-the-loop, validación Pydantic, y control financiero contra loops infinitos). Esto le permitirá especificar un **PRD Agéntico** formal y defender la arquitectura ante comités técnicos internacionales (CTOs).

---

## ⏱️ Agenda de la Sesión (60 Minutos)

| Minutos | Módulo | Diapositivas | Foco Pedagógico |
| :--- | :--- | :--- | :--- |
| **00 - 05 min** | Introducción e Ideación | Slide 1 | Transición de la IA Pasiva (RAG) a la IA Activa (Agentes). |
| **05 - 15 min** | Loops de Razonamiento | Slides 2 - 3 | IA Pasiva vs. Activa y el loop cognitivo ReAct (Thought-Action-Observation). |
| **15 - 30 min** | Patrones y Conectividad | Slides 4 - 6 | Arquitectura Orchestrator-Workers, Tool Calling y optimización de KV Cache. |
| **30 - 45 min** | Caso de Estudio y Estructuras | Slides 7 - 9 | Human-in-the-loop, caso logístico de aduanas/silos y validación Pydantic. |
| **45 - 55 min** | Contención y Redundancia | Slides 10 - 13 | Mitigación de loops infinitos, fallbacks, Mock PRD e integración segura de APIs. |
| **55 - 60 min** | Roleplay y Cierre | Slides 14 - 15 | Preguntas estrella de entrevistas IT, comités de CTOs y consigna semanal. |

---

## 🗺️ Diferencia de Alcance: Sesión 2 vs. Sesión 3 vs. Sesión 4
Para estructurar el discurso de Claudio ante directores de tecnología, contrastamos las sesiones en esta tabla comparativa:

| Eje de Comparación | Sesión 2: IA Pasiva & RAG | Sesión 3: IA Activa & Agentes (Hoy) | Sesión 4: IA a Escala & CI/CD |
| :--- | :--- | :--- | :--- |
| **Foco Pedagógico** | Recuperación e inyección de datos de dominio de forma estática en prompts. | Sistemas que ejecutan acciones, toman decisiones y llaman a APIs externas de forma autónoma. | Evaluación de calidad estadística (Evals), observabilidad y despliegue continuo automatizado. |
| **Arquitectura Clave** | RAG (Chunking + Embeddings + Vector Database). | Loops de razonamiento (ReAct) + Orquestadores + Tool Calling. | Pipelines de monitoreo continuo (Langfuse) + Evals automatizadas en CI/CD. |
| **Dinámica del Bot** | **De Libro Abierto**: El LLM solo lee el material entregado y resume. No altera el mundo externo. | **Ejecutor Autónomo**: El bot puede modificar bases de datos, enviar correos, llamar APIs, etc. | **Auditor y Guardián**: Herramientas que controlan latencia, costos y previenen la degradación del prompt. |
| **Actividad Semanal** | Mock PRD del "Cargill Customs Bot" especificando indexación y umbrales. | PRD y Diagrama de Flujo del Agente de CRM y despachos de Soja en vivo. | Pipeline automatizado de Evals en GitHub Actions con Golden Dataset. |

---

## 🤖 Co-Mentoring Técnico con NotebookLM

> [!TIP]
> Antes de la sesión, pídele a Claudio que suba la guía completa de la mentoría y el manual técnico de la arquitectura a **NotebookLM**. Utilicen el siguiente prompt exacto para simular un copiloto de consultas durante la clase:

```text
Actúa como un CTO y Arquitecto Principal de Inteligencia Artificial de Cargill. Tu objetivo es auditar técnicamente mis propuestas para el "Cargill Logistics Agent" (asistente agéntico de aduanas y silos). Cuando te haga preguntas sobre la implementación de loops ReAct, tool calling, orquestadores, validación con Pydantic o gobernanza de costos por loops infinitos, respóndeme en un tono profesional, pragmático y exigente, contrastando mi rol de Product Manager con la viabilidad real de los sistemas de software agénticos corporativos.
```

---

## 🖋️ Metáforas Visuales para la Pizarra

Dibuja las siguientes analogías en la pizarra en tiempo real para facilitar el entendimiento sin código matemático:

### 1. El Loop de Feedback Cognitivo (ReAct)
```text
         ┌────────────────────────────────────────────────────────┐
         │                                                        │
         ▼                                                        │
┌─────────────────┐      ┌─────────────────┐      ┌───────────────┴─┐
│   Pensamiento   ├─────>│     Acción      ├─────>│   Observación   │
│    (Thought)    │      │    (Action)     │      │  (Observation)  │
│ "Necesito stock│      │   "Query SQL"   │      │ "Silo 4: 500t"  │
└─────────────────┘      └─────────────────┘      └─────────────────┘
```

### 2. Patrón de Diseño Orchestrator-Workers
```text
                    ┌─────────────────────────┐
                    │    Agente Orquestador   │
                    │   (Planifica & Delega)   │
                    └───────────┬─────────────┘
                                │
         ┌──────────────────────┼──────────────────────┐
         ▼                      ▼                      ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Trabajador    │    │   Trabajador    │    │   Trabajador    │
│  (Lector PDFs)  │    │ (Auditor Stock) │    │  (Gestor Email) │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

### 3. Compuerta de Aprobación Human-in-the-Loop (HITL)
```text
[ Flujo Agéntico ] ───> [ ¿Desvío > 10% o Silo Nuevo? ] ──(Sí)──> [ PAUSA / COMPUERTA HITL ] ───> [ Aprobación Humana ] ───> [ ERP ]
                                 │
                                (No)
                                 ▼
                           [ Ejecutar ] ─────────────────────────────────────────────────────────> [ ERP ]
```

### 4. Validación Rígida de Salida (Pydantic slot filter)
```text
[ Entrada LLM Probabilística ] ───> [ Caja de Clasificación Pydantic ] ───> [ JSON Válido Determinista ]
   "Silo 4 tiene unas 500t"                 (Filtro rígido)              {"silo_id": 4, "stock_ton": 500.0}
```

---

## 🛝 Guiones Detallados de las Diapositivas

### 🛝 Slide 1: Portada (Flujos Agénticos Avanzados & IA Activa)
* **Guion**: *"Claudio, bienvenido a la Sesión 3. En nuestro encuentro anterior consolidamos las bases de la IA Pasiva mediante la arquitectura RAG. Aprendiste a inyectar información de forma estructurada para que un modelo de lenguaje actúe bajo el esquema de un examen a libro abierto. Hoy daremos el salto evolutivo más importante del mercado de IA generativa contemporáneo: pasaremos de la 'IA Pasiva' a la 'IA Activa' con Sistemas Agénticos Autónomos. No nos limitaremos a crear bots que respondan preguntas amablemente; diseñaremos sistemas inteligentes capaces de planificar planes de acción, tomar decisiones ejecutivas autónomas e invocar APIs externas de forma dinámica para alterar el mundo real. Imagina esta transición como el paso de un archivero digital que te entrega el manual de regulaciones arancelarias a un analista aduanero proactivo que realiza el trámite ante la aduana, sincroniza el stock en el ERP, genera la documentación de embarque y agenda una reunión en tu calendario. Al terminar esta sesión, sabrás diseñar y especificar diagramas de flujo de agentes autónomos y redactar las reglas de control de costos, Human-in-the-loop y validación estructurada que exigen los directores de tecnología más exigentes a nivel internacional."*
* **🔗 Conexión & Transición**: *"Para comprender el valor de este salto activo, primero debemos contrastar de forma rigurosa la diferencia de alcance frente al RAG estático. Pasemos a la diapositiva 2 para comparar la IA Pasiva frente a la IA Activa."*
* **💡 Tips de Fluidez & Control**:
  * **Tono**: Inspirador, pausado y con mucha autoridad.
  * **Foco**: Haz énfasis en la palabra "Activa". Detente un momento al plantear la analogía del "analista aduanero" para que asimile la proactividad del agente.

### 🛝 Slide 2: IA Pasiva vs. IA Activa (La Transición Evolutiva)
* **Guion**: *"Para liderar proyectos de IA con seniority, debes saber diferenciar ante un comité de tecnología el alcance real de RAG frente a un Agente Autónomo. En la IA Pasiva o RAG tradicional, el sistema está en un estado pasivo de espera: si el usuario no ingresa una consulta, no ocurre nada, y cuando lo hace, el bot se limita a leer documentos indexados y resumirlos en su ventana de contexto. El bot de RAG no puede 'hacer' nada fuera de su pantalla. En cambio, en la IA Activa o Agéntica, el usuario ingresa un objetivo de alto nivel (por ejemplo, 'Sincronizar los despachos de soja pendientes en Rosario y notificar al cliente'). A partir de este objetivo, el modelo no genera solo texto; genera un plan de acción dinámico, realiza llamadas a bases de datos relacionales, consume APIs externas y valida los resultados de sus acciones de forma recursiva hasta alcanzar la meta de negocio. La IA activa altera el estado del negocio."*
* **🔗 Conexión & Transición**: *"Pero para lograr esta proactividad y resolver imprevistos en tiempo real, el sistema debe ser capaz de procesar información, evaluar opciones y decidir el siguiente paso de forma continua. Avancemos a la diapositiva 3 para estudiar el motor de este razonamiento: el loop ReAct."*
* **💡 Tips de Fluidez & Control**:
  * **Tono**: Comparativo y analítico.
  * **Foco**: Usa gestos corporativos para marcar la dualidad "Pasiva" (espera) vs. "Activa" (decisión autónoma). Lee a ritmo constante, sin apurarte.

### 🛝 Slide 3: Loops de Razonamiento: La Arquitectura ReAct (Reason + Act)
* **Guion**: *"La arquitectura cognitiva que permite a un agente actuar con autonomía se conoce como ReAct, propuesto por Yao et al. en 2022. Este patrón divide la ejecución de la IA en un loop recursivo de tres pasos: Pensamiento (Thought), Acción (Action) y Observación (Observation). Miren el gráfico de la diapositiva. Cuando le asignamos un objetivo, el agente primero genera un 'Pensamiento': analiza la meta y deduce qué herramienta necesita. Luego ejecuta una 'Acción': por ejemplo, realizar un query SQL a la tabla de despachos fluviales. El sistema retorna la respuesta de la base de datos, la cual el agente recibe en la 'Observación'. Basándose en esa observación, el agente vuelve al ciclo: genera un nuevo pensamiento sobre si necesita otra acción o si ya alcanzó el objetivo para emitir la respuesta final. **Pensá en este loop bajo la analogía de un operario de mantenimiento de una central de energía**: ante una alerta, el operario piensa qué válvula inspeccionar, camina y gira la válvula (Acción), lee el medidor de presión (Observación) y, basándose en esa lectura, piensa si debe girar otra válvula o si la presión se ha estabilizado. El agente opera con esa misma dinámica interactiva en milisegundos."*
* **🔗 Conexión & Transición**: *"Este loop funciona a la perfección para tareas aisladas, pero al escalar el sistema a múltiples departamentos, un único agente colapsaría por saturación. Avancemos a la diapositiva 4 para ver cómo organizamos este trabajo en equipos agénticos mediante el patrón Orchestrator-Workers."*
* **💡 Tips de Fluidez & Control**:
  * **Interacción**: Haz clic en el diagrama interactivo de ReAct de la diapositiva para mostrar cada paso (Pensamiento -> Acción -> Observación) a medida que los mencionas.
  * **Tono**: Pedagógico y pausado. Asegúrate de que entienda la analogía del operario.

### 🛝 Slide 4: Patrones de Diseño Agénticos: Orchestrator-Workers & Routing
* **Guion**: *"Al escalar sistemas agénticos corporativos, un único agente monolítico colapsará debido a la saturación de su ventana de contexto y a la variabilidad probabilística. Por ello, la arquitectura de vanguardia en 2026 se basa en patrones multi-agente, siendo el modelo **Orchestrator-Workers** (Orquestador y Trabajadores) el estándar enterprise. En este patrón, tenemos un agente Orquestador central encargado exclusivamente de fragmentar el objetivo del negocio en tareas menores y delegarlas a agentes Trabajadores especializados. Cada Trabajador tiene un prompt ultra-enfocado, un subset de herramientas limitado y un rol específico (ej. un especialista en SQL, otro en APIs de aduanas y otro en redactar correos). **Pensalo como la distribución de trabajo en una terminal portuaria**: no tenés a un único empleado manejando la grúa, cobrando las tarifas, firmando los recibos aduaneros y cargando los barcos simultáneamente (colapsaría). En cambio, tenés un Coordinador de Puerto (el Orquestador) que delega tareas específicas al Operador de Grúa, al Analista de Aduanas y al despachante logístico (los Trabajadores especializados). Esto reduce el ruido semántico y garantiza que cada tarea sea resuelta con máxima precisión y mínimos costos de cómputo."*
* **🔗 Conexión & Transición**: *"Ahora, ¿cómo interactúan estos trabajadores especializados con los sistemas reales de la terminal portuaria para ejecutar las órdenes físicas? Pasemos a la diapositiva 5 para ver la tecnología detrás de esta conectividad: el Tool Calling."*
* **💡 Tips de Fluidez & Control**:
  * **Interacción**: Haz clic en los diferentes perfiles de trabajadores (Lector PDFs, Auditor Stock, etc.) para que se vea la interactividad de la diapositiva.
  * **Foco**: Recálcale a Claudio que el orquestador delega pero no ejecuta, y que esto reduce la probabilidad de errores.

### 🛝 Slide 5: Tool Calling: Invocar APIs Externas de Forma Dinámica
* **Guion**: *"La funcionalidad que conecta a la IA con el mundo real se denomina **Tool Calling** (Llamada a Herramientas). Los desarrolladores declaran un listado de funciones en formato JSON Schema al modelo de lenguaje (por ejemplo: consultar stock, enviar email o calcular aranceles). El LLM no ejecuta el código directamente (las APIs de OpenAI o Google no pueden conectarse a la base de datos de tu empresa por seguridad). En su lugar, el modelo decide de forma probabilística qué función es relevante y devuelve un JSON que especifica el nombre de la herramienta y los argumentos exactos necesarios. El servidor backend de tu empresa lee este JSON, ejecuta la función real de forma determinista y segura, y le devuelve el resultado en texto al modelo para que continúe su análisis. **Pensalo como un panel de control con interruptores electrónicos en una cabina ferroviaria**: el maquinista (el LLM) no sale físicamente de la cabina a mover las vías de hierro con sus manos; simplemente presiona el botón eléctrico 'Cambio de Vía 4' (JSON de Tool Call) y el sistema de automatización física del tren (el backend de la empresa) realiza el movimiento físico en las vías y le enciende una luz verde de confirmación en la cabina (Observación del resultado). Esto nos permite inyectar automatización de alto rendimiento sin comprometer la seguridad física del sistema."*
* **🔗 Conexión & Transición**: *"Sin embargo, cuando el agente interactúa en loops recursivos llamando a APIs secundarias, el rendimiento y la velocidad de respuesta pueden degradarse significativamente. Avancemos a la diapositiva 6 para comprender cómo optimizamos la latencia en agentes mediante el KV Cache."*
* **💡 Tips de Fluidez & Control**:
  * **Tono**: Explicativo y técnico-comercial. Suena natural y seguro al mencionar "JSON Schema".
  * **Interacción**: Utiliza el botón interactivo de simulación en la consola de la slide para mostrar cómo la petición del LLM se transforma en una ejecución de API real.

### 🛝 Slide 6: Latencia y Eficiencia en Agentes: Optimización de KV Cache
* **Guion**: *"Desarrollar agentes autónomos introduce un desafío crítico en la experiencia del usuario: la **latencia**. Dado que el loop ReAct requiere múltiples pasadas consecutivas por el modelo de lenguaje (Thoughts y Actions), si cada llamada de inferencia debe re-procesar todo el historial de la conversación desde el inicio en el hardware de la nube, el sistema tardará decenas de segundos en responder. Para mitigar esto, los ingenieros de infraestructura optimizan el **KV Cache** (Key-Value Cache). Esta tecnología almacena de forma persistente las representaciones matemáticas de las consultas y respuestas previas en los chips GPU de los servidores de la nube, evitando que la IA tenga que recalculadoras matemáticas de todo el texto en cada iteración del loop. **Pensalo bajo la analogía de la memoria de corto plazo de un operador portuario en plena crisis**: si en cada llamada del coordinador de puerto el operador tuviera que leer de vuelta las 50 páginas del manual de exportaciones desde la primera línea para responder una pregunta complementaria menor, la operación se detendría por completo. En su lugar, el operador mantiene el manual abierto sobre su escritorio y las páginas relevantes memorizadas en su cabeza (KV Cache), permitiéndole responder al instante las consultas sucesivas. Habilitar la optimización de KV Cache reduce la latencia de primer token en más de un 60%, haciendo viable el uso de agentes en interfaces comerciales en tiempo real."*
* **🔗 Conexión & Transición**: *"Optimizar el tiempo de respuesta es vital para el usuario, pero dar autonomía total a una IA probabilística para alterar bases de datos transaccionales conlleva riesgos críticos de negocio. Pasemos a la diapositiva 7 para analizar la compuerta de seguridad fundamental: el Human-in-the-loop."*
* **💡 Tips de Fluidez & Control**:
  * **Foco**: El concepto clave es que el KV Cache evita repetir cálculos. Úsalo como un argumento de eficiencia de costos que Claudio puede esgrimir ante ingenieros.
  * **Tono**: Firme y corporativo.

### 🛝 Slide 7: Human-in-the-Loop: Compuertas de Supervisión Humana
* **Guion**: *"Una regla de gobernanza mandatoria en la implementación de IA empresarial es la integración de **Human-in-the-loop** (HITL). La autonomía total del agente es excelente para tareas informativas, pero en flujos críticos de negocio —como emitir una transferencia bancaria o autorizar el despacho fluvial de un buque de granos—, delegar el 100% de la firma a una IA probabilística es un riesgo inaceptable para el negocio. Por ello, diseñamos compuertas lógicas en el backend donde el agente suspende su ejecución, guarda su estado en memoria y envía una notificación de aprobación al usuario humano antes de ejecutar una acción de alto impacto. **Pensalo como el protocolo de dos llaves en un silo de misiles o en una bóveda de alta seguridad**: el oficial de automatización (el agente de IA) puede preparar los sistemas y cargar las coordenadas de destino de forma precisa, pero el lanzamiento real exige que el comandante de la base (el humano supervisor) inserte y gire físicamente su llave en el tablero de control. El agente prepara el reporte de aranceles y la orden de despacho, pero la firma comercial definitiva que valida la transacción requiere el Sign-Off de un empleado humano. Esto nos permite beneficiarnos del 95% de velocidad de preparación del agente, manteniendo el control de riesgos de negocio en el 5% final de la ejecución."*
* **🔗 Conexión & Transición**: *"Establecidas estas barreras de seguridad humana, veamos cómo se integran todos estos componentes (ReAct, Orquestadores y HITL) en un escenario portuario real. Avancemos a la diapositiva 8 para estudiar nuestro caso de estudio logístico fluvial."*
* **💡 Tips de Fluidez & Control**:
  * **Tono**: Enérgico y centrado en la mitigación de riesgos de negocio.
  * **Interacción**: Haz clic en el botón de "Simular Aprobación Humana" para mostrar al alumno cómo la compuerta HITL suspende el flujo y espera la acción manual.

### 🛝 Slide 8: Caso de Estudio: Logística Fluvial y Despacho de Granos
* **Guion**: *"Apliquemos toda esta arquitectura de IA Activa sobre un caso de estudio corporativo de alto impacto: la automatización logística y despacho portuario de soja. Imaginemos que una barcaza arriba a la terminal fluvial. El agente recibe de forma automática el manifiesto de carga en PDF, extrae los datos clave y detecta que el cargamento supera la capacidad del silo asignado originalmente. En lugar de limitarse a alertar al operador (IA Pasiva), el agente inicia un flujo activo: consulta la disponibilidad de espacio en silos alternativos mediante una API interna, verifica las restricciones de calado del canal, genera una propuesta de reasignación óptima y la envía a través de una API de mensajería (Slack/Teams) al coordinador del puerto para su firma electrónica (Human-in-the-loop). Una vez que el humano presiona 'Aprobar', el agente ejecuta de forma autónoma la actualización de stock en el ERP corporativo y solicita el permiso de descarga correspondiente al sistema aduanero de forma automatizada. Este caso de estudio demuestra cómo la IA Activa elimina cuellos de botella operativos en la cadena de suministro tradicionales, optimizando los tiempos de rotación de las barcazas y reduciendo costos por estadía portuaria en un 30%."*
* **🔗 Conexión & Transición**: *"En este flujo logístico fluvial, el agente extrajo las toneladas y propuso reubicar la barcaza. Pero para que el ERP entienda estas actualizaciones, el formato de salida debe ser estrictamente estructurado, no texto plano. Pasemos a la diapositiva 9 para analizar la validación estructurada del esquema de datos."*
* **💡 Tips de Fluidez & Control**:
  * **Interacción**: Muestra el mapa esquemático interactivo a la derecha, señalando cómo se visualizan las barcazas y silos en tiempo real mediante la recomendación de la IA.
  * **Foco**: Conecta el caso con la reducción de costos operativos (estadías de barcos).

### 🛝 Slide 9: Validación Estructurada (Esquema de Datos)
* **Guion**: *"Cuando conectas un agente de IA con sistemas legados o ERPs corporativos de base relacional, no puedes permitir que el bot devuelva texto plano redactado de forma libre como: 'El stock disponible de soja es de aproximadamente 500 toneladas en el silo 4'. Los sistemas tradicionales no entienden aproximaciones literarias; exigen variables estrictas con tipos de datos definidos. Como Product Manager de IA, tu rol no es escribir el código en Python; tu deber es definir la **Especificación de Reglas de Negocio (DoD)** y las tolerancias en el PRD —como los campos, tipos y límites numéricos de validación— para que el equipo de desarrollo configure los validadores de esquema de datos (como Pydantic y JSON Schema) en el backend. **Pensalo como la ranura de clasificación física en una caja de ahorro infantil o en una máquina expendedora de monedas**: no importa el ángulo en que introduzcas la moneda de $1, la ranura física solo permite el paso de objetos con las dimensiones de circunferencia y espesor exactos exigidos por el mecanismo metálico, rechazando al instante cualquier moneda defectuosa o de otra denominación. Pydantic actúa como esa ranura metálica en el software: define la estructura rígida de datos exigida por el ERP y, si la IA intenta devolver un dato mal formateado o con campos incompletos, el validador del backend intercepta el fallo en milisegundos, bloquea el paso de datos al sistema de producción, y le reenvía una instrucción de corrección automática a la IA con el log de error para que reformatee la salida de inmediato. Esto garantiza la integridad transaccional de los sistemas de producción."*
* **🔗 Conexión & Transición**: *"Garantizar que el sistema reciba un formato estructurado e intente auto-corregirse ante errores es fantástico, pero permitir que el agente itere de forma indefinida en loops autónomos ante fallas persistentes de APIs plantea riesgos de facturación financiera incontrolables. Avancemos a la diapositiva 10 para explorar el control de costos y la mitigación de loops infinitos."*
* **💡 Tips de Fluidez & Control**:
  * **Tono**: Explicativo, centrado en el rol del PM en la definición de especificaciones de datos.
  * **Interacción**: Haz clic en el botón interactivo "Alternar Entrada Cruda" en el simulador de la slide para demostrar la diferencia visual entre la salida libre alucinada y el JSON estructurado y validado.

### 🛝 Slide 10: Control de Costos en IA Activa: Mitigación de Loops Infinitos
* **Guion**: *"La IA activa introduce un riesgo financiero nuevo y sumamente crítico: los **loops infinitos** en la toma de decisiones agénticas. Dado que el loop ReAct evalúa de forma autónoma el resultado de sus acciones en cada paso, si un agente encuentra una inconsistencia en un API (por ejemplo, una llamada que retorna un código de error de base de datos) y su prompt le indica corregir el error por sí mismo, el agente podría ingresar en un loop recursivo infinito llamando a la API de OpenAI 10,000 veces consecutivas en pocos minutos intentando descifrar el error. Esto puede generar facturas de miles de dólares de consumo en tu tarjeta corporativa en una sola noche de forma descontrolada. Para evitar esto en Cargill, como PM debes exigir en las especificaciones del backend tres limitadores físicos rigurosos: 1) **Límite máximo de iteraciones** (Max Iterations de 5 a 7 llamadas consecutivas por sesión de usuario). 2) **Timeouts estrictos de ejecución de API** (ej. cancelar la sesión agéntica si el flujo total tarda más de 15 segundos). 3) **Alertas de presupuesto en tiempo real** conectadas a compuertas de parada en el backend. **Pensalo como configurar el límite de consumo diario de datos y de roaming en tu celular antes de viajar al extranjero**: no importa si tu teléfono intenta descargar videos o actualizaciones en segundo plano de forma automática; el operador telefónico de la red corta el flujo de internet al alcanzar el límite de gigabytes preestablecido, evitando sorpresas catastróficas en la factura de fin de mes. Implementar estos cortafuegos en tu especificación funcional del PRD blinda los presupuestos de nube de la corporación."*
* **🔗 Conexión & Transición**: *"Controlar el presupuesto mediante limitadores rígidos blinda al negocio, pero si una API clave se cae permanentemente, el agente no debe quedarse congelado en pantalla ni arrojar un error técnico crudo. Pasemos a la diapositiva 11 para ver el diseño de Fallbacks y resiliencia de sistemas."*
* **💡 Tips de Fluidez & Control**:
  * **Tono**: Alerta y de advertencia financiera.
  * **Interacción**: Ejecuta la simulación de loop en la diapositiva para que se visualice cómo el backend interrumpe la ejecución con el aviso "LOOP LIMITADO A 5 ITERACIONES".

### 🛝 Slide 11: Resiliencia y Fallbacks: Gestión de Caídas de Sistemas en Agentes
* **Guion**: *"En la ingeniería de software moderna, la pregunta crítica para un Project Manager no es '¿cómo funciona el sistema cuando todo está online?', sino '¿cómo reacciona tu producto de forma controlada cuando un sistema crítico externo se cae?'. Si tu agente de aduanas de IA intenta consultar el calado de la hidrovía en tiempo real para autorizar un despacho, pero el servidor del organismo nacional está caído o no responde por mantenimiento de red, el agente no debe quedarse congelado en pantalla ni arrojar un error técnico de bajo nivel al usuario. Debemos diseñar **Fallbacks deterministas**. Un fallback es un plan de contingencia codificado de antemano que intercepta el fallo de la herramienta agéntica y redirige el flujo de forma segura. **Pensalo como el protocolo de desvío de tráfico terrestre ante la clausura de un puente por obras**: si la vía principal está cortada, las señales de tránsito desvían a todos los camiones de forma automática por una ruta secundaria habilitada para que sigan circulando, o detienen los camiones en un puesto de control seguro informándoles la causa del retraso. En el Cargill Customs Bot, si la API del organismo nacional falla, el agente activa el fallback: lee una base de datos histórica local guardada en caché (con datos de hace 24 horas) y emite una alerta indicando que trabaja con datos de respaldo históricos, o escala inmediatamente el flujo a un analista logístico humano mediante un ticket de urgencia de soporte. Diseñar estos desvíos lógicos garantiza la resiliencia operativa y la reputación de tu producto de tecnología ante incidentes inesperados."*
* **🔗 Conexión & Transición**: *"Con estos mecanismos de contención, resiliencia y gobernanza claros, es hora de plasmar estas reglas de negocio en la documentación oficial de producto. Avancemos a la diapositiva 12 para iniciar nuestro taller práctico de diseño del Mock PRD."*
* **💡 Tips de Fluidez & Control**:
  * **Tono**: Seguro, analítico y centrado en la resiliencia operativa.
  * **Interacción**: Haz clic en el botón de simular caída de la API en la slide para que el alumno visualice de qué manera el agente redirige el flujo hacia la base de datos histórica local de forma transparente.

### 🛝 Slide 12: Taller: Mock PRD del Agente de Logística y Despachos
* **Guion**: *"Pasemos a la acción práctica en nuestro taller. Claudio, en esta actividad daremos forma al Mock PRD del 'Cargill Logistics Agent'. En este documento de requerimientos de producto no especificaremos una base vectorial estática; daremos estructura y reglas lógicas de negocio al sistema de agentes de la central. En primer lugar, definiremos el alcance del Orquestador central y sus tres Trabajadores especializados: el Analista de Documentos, el Auditor de Silos y el despachante de Emails. En segundo lugar, estableceremos las **herramientas autorizadas** para cada rol (por ejemplo, el Lector de Documentos tiene prohibido acceder a la API de facturación por seguridad). Y en tercer lugar, especificaremos de forma estricta las compuertas de **Human-in-the-loop**: cualquier desvío de carga de barcazas mayor al 10% de tolerancia respecto al volumen planificado, o cualquier cambio en el silo de destino, exigirá la firma de aprobación electrónica de un supervisor del puerto antes de ser procesado de forma definitiva en el ERP corporativo. Este PRD de Session 3 será la joya de tu portafolio en LinkedIn, demostrando a los reclutadores de tecnología que dominás el diseño detallado de sistemas de IA empresarial de alto impacto."*
* **🔗 Conexión & Transición**: *"Una vez estructurados los requerimientos funcionales en nuestro PRD, debemos comprender la topología física de integración de estos agentes con nuestros sistemas centrales sin comprometer la seguridad. Pasemos a la diapositiva 13 para analizar la arquitectura de integración de datos."*
* **💡 Tips de Fluidez & Control**:
  * **Foco**: Enfatiza que este taller es para diseñar la gobernanza y los límites lógicos, demostrando su seniority directivo en LinkedIn y entrevistas.
  * **Tono**: Motivador, guiando al alumno paso a paso por los tres bloques de la especificación.

### 🛝 Slide 13: Arquitectura de Integración: Del Agent a las APIs Transaccionales
* **Guion**: *"Un error de ciberseguridad catastrófico que cometen las startups de IA es permitir que los agentes escriban o editen registros directamente en la base de datos de producción de la compañía de forma directa sin filtros intermedios. Los agentes de IA son probabilísticos y, ante un error en su razonamiento semántico, un agente podría ejecutar un comando de borrado masivo de filas o escribir valores de stock de soja negativos en tu base de datos relacional relacional de producción. Por ende, la arquitectura de integración corporativa madura exige que **los agentes interactúen con los sistemas centrales exclusivamente a través de una capa intermedia de APIs internas controladas** (API Gateway). **Pensalo como el protocolo de seguridad de un laboratorio biológico de alta seguridad**: los científicos de la sala principal (el agente de IA) no tocan directamente los virus o reactivos altamente peligrosos en los estantes con sus manos desnudas; interactúan a través de cabinas aisladas selladas al vacío utilizando guantes mecánicos fijos y filtros de aire automáticos (APIs intermedias) que controlan la presión y el flujo del material, aislando por completo la cabina de experimentos de la atmósfera exterior del edificio. En tu arquitectura agéntica, si el bot necesita registrar un despacho, envía un JSON con los datos estructurados a una API de validación de backend. Esta API (el guante mecánico) verifica que el ID del puerto exista, que las toneladas sean números válidos superiores a cero y que la transacción sea válida de acuerdo con las reglas deterministas de software, realizando recién allí el guardado definitivo en la base de datos SQL. Implementar esta separación física de arquitecturas de integración protege la estabilidad de los sistemas centrales de tu empresa."*
* **🔗 Conexión & Transición**: *"Esta arquitectura de integración blinda nuestros sistemas core de producción. Pero para consolidar este seniority ante reclutadores y CTOs en un proceso de entrevista real, debemos saber argumentar estas decisiones bajo presión. Avancemos a la diapositiva 14 para iniciar nuestro Roleplay y simulación de comités de tecnología."*
* **💡 Tips de Fluidez & Control**:
  * **Tono**: De advertencia técnica y seguridad arquitectónica.
  * **Foco**: Claudio debe entender que un agente jamás interactúa directo con una base de datos de producción; la capa de APIs intermedias es mandatoria.

### 🛝 Slide 14: Roleplay: Defensa Técnica de IA en Entrevistas (CTO Audit)
* **Guion**: *"Hagamos una simulación de comité técnico de alto impacto. Imagina que un **CTO** internacional te interroga en una entrevista de trabajo estratégica: 'Tenemos un agente de IA enviando correos automatizados de cotización a clientes. Anteayer un cliente inyectó un comando malicioso en el cuerpo del correo y forzó al bot a enviarle una oferta con un descuento del 90%. ¿Cómo solucionaría este fallo de seguridad catastrófico en la arquitectura?'. Tu respuesta inmediata debe ser un rotundo: 'Implementando un validador de formato de salida estructurado (JSON Schema/Pydantic) acoplado a una compuerta de aprobación de Human-in-the-loop'. Explicás al CTO que el error consistió en dar autonomía total de salida de texto plano y ejecución al agente sin filtros intermedios. La solución técnica radica en: 1) Forzar al bot a responder exclusivamente en variables numéricas estructuradas, impidiendo que el bot redacte o altere el cuerpo del contrato de forma libre. 2) Establecer un motor de reglas en el backend que compare los precios emitidos por la IA contra las tarifas oficiales históricas guardadas en la base de datos de Cargill. 3) Si la propuesta de descuento supera el 10% de tolerancia máxima permitida, el sistema suspende de forma automatizada el envío, bloquea la inferencia e ingresa el ticket al panel de control de un gerente comercial humano para su firma electrónica de Sign-Off. Esta defensa técnica demuestra que no solo entiendes la IA generativa como un experimento, sino que dominas el control de riesgos de negocio corporativos y la gobernanza de datos enterprise. Dominar este discurso técnico ante reclutadores internacionales te consagra como un AI Project Manager de élite."*
* **🔗 Conexión & Transición**: *"Esta defensa técnica demuestra que posees el nivel conceptual y pragmático para liderar despliegues de IA a escala. Para concluir la sesión de hoy y proyectar el cierre del programa, avancemos a la diapositiva 15 para revisar la hoja de ruta y la consigna semanal."*
* **💡 Tips de Fluidez & Control**:
  * **Tono**: Dinámico, actuando el juego de roles con energía.
  * **Foco**: Refuerza en el alumno la importancia de los tres pilares de defensa: salida estructurada, comparación contra base de datos core y compuerta HITL.

### 🛝 Slide 15: Tu Ruta y Valor como Project Manager de IA Activa
* **Guion**: *"Claudio, felicitaciones por completar esta intensa Sesión 3. Hoy diste el gran salto conceptual hacia la IA Activa y el diseño agéntico autónomo. Comprender los loops de razonamiento ReAct te capacita para liderar comités de diseño de sistemas autónomos; dominar el diseño multi-agente en el patrón Orchestrator-Workers te otorga autoridad técnica para coordinar y planificar sprints con arquitectos de datos; y entender el control de costos de loops infinitos, validaciones Pydantic y compuertas Human-in-the-loop te posiciona en la cima del mercado como un Project Manager capaz de gobernar los riesgos operativos de la compañía. In nuestra hoja de ruta: hoy en la Sesión 3 dominamos el diseño de la 'IA Activa' mediante agentes autónomos y coordinamos sus integraciones con APIs corporativas. En nuestra próxima y última sesión, la Sesión 4, daremos el cierre definitivo: analizaremos los Economics de la IA Generativa, calcularemos el ROI de estas implementaciones, estructuraremos pipelines de **Evals automatizadas** en entornos de CI/CD para que el bot corra crash-tests semánticos en cada commit, y simularemos una auditoría técnica completa para que salgas al mercado laboral internacional con la máxima confianza y seniority técnico del mercado actual. ¡Excelente semana de trabajo, completa el PRD agéntico en GitHub y nos vemos en la Sesión 4!"*
* **💡 Tips de Fluidez & Control**:
  * **Tono**: Altamente motivador, felicitando el progreso y marcando el final de la sesión en un punto alto de energía.
  * **Foco**: Recomienda al alumno consolidar el PRD agéntico para presentarlo en la Sesión 4."*
