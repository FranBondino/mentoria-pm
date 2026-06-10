# 📚 Glosario Estratégico de Elite: Sesión 3 — IA Activa & Agentes Autónomos

Este glosario técnico y de negocio está diseñado para Product Managers que necesitan dominar la frontera entre la IA estática y los nuevos sistemas de IA Activa (Agentes) a nivel corporativo.

---

## 🚀 Bloque 1: Arquitectura Cognitiva y Agentes

### 1. IA Activa (Agentes Autónomos)
*   **Definición Técnica Extensa**: A diferencia de la IA Pasiva (RAG), que solo devuelve texto, la **IA Activa** integra un "motor de razonamiento" que le permite interactuar con el entorno. Un agente puede llamar APIs, ejecutar código, modificar bases de datos y gestionar flujos de trabajo de principio a fin para alcanzar una meta definida.
*   **Insight del PM**: Tu planificación de backlog cambia: ya no pedís "pantallas", pedís "capacidades operativas" (herramientas) que el agente usará para resolver el problema solo.

### 2. Loop ReAct (Reason + Act)
*   **Definición Técnica Extensa**: Arquitectura que obliga al modelo a alternar entre pasos de pensamiento explícito y acciones técnicas. Se basa en tres etapas: **Thought** (el agente verbaliza su plan), **Action** (invoca una herramienta) y **Observation** (lee el resultado de esa herramienta para decidir el siguiente paso).
*   **Insight del PM**: Es vital para la **explicabilidad**. Si el agente comete un error, podés revisar el "log de pensamientos" para ver exactamente dónde se desvió su lógica.

### 3. Patrón Orchestrator-Workers
*   **Definición Técnica Extensa**: Diseño multi-agente donde un "Orquestador" central descompone el pedido del usuario en subtareas y las delega a "Workers" especializados (ej. un lector de balances, un auditor de SQL). El orquestador luego ensambla todas las respuestas en un resultado final consolidado.
*   **Insight del PM**: Este patrón reduce drásticamente las alucinaciones al permitir que cada agente se enfoque en una tarea atómica y use solo las herramientas que necesita para ese paso.

---

## 🛠️ Bloque 2: Integración y Validación Técnica

### 4. Pydantic
*   **Definición Técnica Extensa**: Es la librería líder en Python para la **validación de datos** mediante el uso de anotaciones de tipo. En IA, se usa para obligar al LLM a que su respuesta cumpla estrictamente con un esquema definido, lanzando un error si falta un campo o si el formato es incorrecto.
*   **Metáfora**: Es el "oficial de cumplimiento" de los datos. No importa lo que el agente quiera mandar; si el documento no tiene el sello y los campos tal cual los pide el sistema, Pydantic lo rebota y le exige a la IA que lo corrija.

### 5. JSON Schema
*   **Definición Técnica Extensa**: Es un vocabulario declarativo que permite anotar y validar documentos JSON. Define la estructura y los tipos de datos. Es el **contrato** que firmás entre el modelo de IA y tu backend para asegurar que hablen el mismo idioma técnico.

### 6. Tool Calling (Invocación de Funciones)
*   **Definición Técnica Extensa**: Capacidad de un modelo para generar instrucciones estructuradas (JSON) que indican qué herramienta externa quiere usar. El modelo no "hace" la acción; emite el pedido técnico para que tu sistema la ejecute de forma segura.

---

## 🛡️ Bloque 3: Gobernanza, Observabilidad y Riesgo

### 7. Langfuse / Phoenix (Observabilidad)
*   **Definición Técnica Extensa**: Herramientas especializadas que permiten monitorear el ciclo de vida completo de una interacción con la IA. Permiten rastrear trazas de ejecución, medir costos de tokens, evaluar la latencia y capturar el feedback del usuario.
*   **Insight del PM**: Estas herramientas son tus mejores amigas. Te permiten ver los logs reales, entender dónde fallan los agentes y justificar los costos de infraestructura ante gerencia con datos duros.

### 8. API Gateways (Capa de Aislamiento)
*   **Definición Técnica Extensa**: Un servidor intermedio que actúa como única puerta de entrada para las peticiones de la IA hacia tus sistemas. Valida, filtra y audita cada solicitud, asegurando que la IA nunca toque los datos de producción de forma directa.
*   **Metáfora**: Es el cajero blindado del banco. Vos le pasás el cheque por la ranura (el Gateway), él verifica todo y recién ahí saca la plata de la bóveda (tu base de datos).

### 9. Human-in-the-loop (HITL)
*   **Definición Técnica Extensa**: Mecanismo de control donde el agente pausa su ejecución y solicita aprobación humana antes de realizar una acción crítica, cara o irreversible (ej. emitir un pago).

### 10. Guardrails (Vallas de Seguridad)
*   **Definición Técnica Extensa**: Sistemas de filtrado que actúan como una capa exterior al modelo. Bloquean inputs ofensivos del usuario o impiden que el modelo responda sobre temas que no son de su incumbencia.

---

## 🧠 Bloque 4: Optimización y Memoria

### 11. KV Cache
*   **Definición Técnica Extensa**: Técnica que guarda en memoria GPU los cálculos de las partes del prompt que no cambian. Esto reduce drásticamente el tiempo de respuesta (TTFT) y baja los costos.

### 12. Gestión de Estado (Memoria Corto/Largo Plazo)
*   **Definición Técnica Extensa**: Habilidad del agente para retener contexto. **Corto Plazo**: Historial del chat actual. **Largo Plazo**: Información guardada en bases vectoriales que el agente puede recuperar meses después.

### 13. Reasoning Tokens (Tokens de Pensamiento)
*   **Definición Técnica Extensa**: Nuevos modelos (como o1) que utilizan tokens internos para "pensar" el problema antes de responder. Estos tokens permiten resolver quilombos lógicos y matemáticos mucho más complejos.

### 14. Max Iterations / Timeouts
*   **Definición Técnica Extensa**: Cortafuegos lógicos que limitan cuántas veces el agente puede intentar resolver un paso. Evita que el agente entre en un "bucle infinito" de llamadas a la API que consuma todo tu presupuesto.
