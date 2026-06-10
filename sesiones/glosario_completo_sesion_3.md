# 📚 Glosario de Re-Entry Tecnológico: Sesión 3 & IA Activa / Agentes Autónomos

Este glosario ha sido diseñado especialmente para **Product Managers y Líderes de Producto** que necesitan cerrar la brecha entre la IA estática (RAG) y los nuevos sistemas de IA Activa (Agentes Autónomos) a nivel corporativo.

Cada término incluye:
*   **Definición Técnica Simplificada**: El concepto real sin tecnicismos innecesarios.
*   **Metáfora / Ejemplo de la Vida Real**: Para anclar el conocimiento de forma intuitiva.
*   **Enfoque PM (¿Por qué te importa?)**: La implicancia estratégica de este concepto al gestionar equipos, priorizar backlogs y mitigar riesgos operativos.

---

## 🚀 Bloque 1: Arquitectura Cognitiva y Agentes

### 1. IA Pasiva (RAG Clásico)
*   **Definición Técnica Simplificada**: Sistemas basados en Retrieval-Augmented Generation donde el bot solo responde preguntas leyendo documentos inyectados en su contexto, pero no tiene capacidad de modificar el mundo exterior o ejecutar acciones.
*   **Metáfora**: Un bibliotecario experto que te busca el libro exacto y te lee un resumen del párrafo, pero no puede firmar un cheque ni comprar un libro nuevo por vos.
*   **Enfoque PM**: Es seguro y determinista en su impacto, excelente para bases de conocimiento, pero está limitado por el "sandbox de la pantalla". No altera bases de datos ni interactúa con sistemas externos de forma activa.

### 2. IA Activa (Sistemas Agénticos / Agentes Autónomos)
*   **Definición Técnica Simplificada**: Sistemas donde el modelo de lenguaje (LLM) tiene autonomía para llamar APIs externas, ejecutar código y modificar registros basándose en un objetivo general, tomando decisiones dinámicas paso a paso.
*   **Metáfora**: Un empleado al que le indicás "resolvé este problema logístico". Él mismo decide a quién llamar, qué correos enviar y en qué momento terminar la tarea de manera autónoma.
*   **Enfoque PM**: Cambia el paradigma del producto. Ya no diseñás flujos pantalla a pantalla de forma rígida, sino que definís el "objetivo de negocio", las herramientas operativas permitidas y las barreras de seguridad (guardrails) para que el agente opere sin romper nada.

### 3. Loop ReAct (Reasoning and Acting)
*   **Definición Técnica Simplificada**: Una arquitectura cognitiva fundacional que obliga al agente a iterar en tres pasos cíclicos: Pensamiento (Thought), Acción (Action) y Observación (Observation) antes de dar una respuesta final.
*   **Metáfora**: Un mecánico reparando un motor. Piensa: "Podría ser la batería" (Thought), prueba conectando un voltímetro (Action), lee que el voltaje es nulo (Observation) y luego decide el siguiente paso.
*   **Enfoque PM**: Es el motor interno de la autonomía. Te ayuda a entender por qué el agente a veces tarda más en responder: está "pensando en voz alta" e interactuando con sistemas en bucle interno antes de presentarte un resultado consolidado.

### 4. Patrón Orchestrator-Workers (Orquestador y Trabajadores)
*   **Definición Técnica Simplificada**: Un diseño multi-agente donde un "Orquestador" central recibe la meta compleja, define un plan y delega micro-tareas a múltiples "Trabajadores" especializados (ej. un lector de PDFs, un auditor SQL), ensamblando luego el resultado.
*   **Metáfora**: Un Director de Proyecto (Orquestador) que recibe el pedido de un cliente y asigna tareas específicas al diseñador, al programador y al QA (Trabajadores), coordinando la entrega sin hacer el trabajo mecánico.
*   **Enfoque PM**: Permite escalar la fiabilidad del software corporativo. En lugar de tener un solo "super bot generalista" propenso a errores, creás perfiles de IA hiper-especializados con responsabilidades aisladas, acotadas y más seguras.

---

## 🛠️ Bloque 2: Integración, Gobernanza y Costos

### 5. Tool Calling (Invocación Dinámica de APIs)
*   **Definición Técnica Simplificada**: La capacidad de un LLM de no responder con texto libre, sino de devolver un objeto JSON estructurado indicando qué función externa (API) quiere ejecutar y con qué parámetros exactos.
*   **Metáfora**: Un operador de planta que, en lugar de relatar por radio la presión de una caldera, presiona botones específicos en un tablero de control para abrir válvulas de descompresión automáticamente.
*   **Enfoque PM**: Es el puente entre el razonamiento probabilístico (IA) y el backend determinista de tu empresa. Como PM, tu tarea es definir el "JSON Schema" de las herramientas (qué botones existen, para qué sirven y qué variables requieren).

### 6. KV Cache (Optimización de Latencia)
*   **Definición Técnica Simplificada**: Una técnica de memoria en la GPU que almacena los cálculos matemáticos de las partes del prompt que no cambian entre turnos de una conversación, evitando reprocesar todo el historial.
*   **Metáfora**: Un mozo que recuerda tu nombre y lo que pediste de entrada, para no tener que preguntarte toda la historia de la mesa cada vez que se acerca a ofrecerte el postre.
*   **Enfoque PM**: Reduce drásticamente el "Time to First Token" (TTFT) en loops sucesivos de ReAct y abarata los costos computacionales (hasta un 60% menos), volviendo viables económicamente a los agentes que "piensan mucho".

### 7. Human-in-the-Loop (HITL)
*   **Definición Técnica Simplificada**: Un mecanismo de seguridad (compuerta lógica) que pausa temporalmente el flujo autónomo de un agente y requiere la aprobación manual de un operador humano antes de ejecutar una acción crítica.
*   **Metáfora**: El botón rojo de un misil que requiere que dos generales giren una llave física antes del lanzamiento, impidiendo que la computadora tome la decisión irreversible por su cuenta.
*   **Enfoque PM**: Es tu principal herramienta de Gobernanza y Control de Riesgos. Permite introducir agentes en flujos core del negocio. Definir dónde poner estas compuertas (ej. para pagos mayores a $10k USD) es el trabajo clave del PM en la era de IA.

### 8. Validación Estructurada (Pydantic / JSON Schema)
*   **Definición Técnica Simplificada**: El uso de librerías (como Pydantic) en el backend para verificar que los datos generados por el agente cumplan estrictamente con los tipos de datos esperados (ej. que "silo_id" sea un número entero y no un string) antes de procesarlos.
*   **Metáfora**: Un guardia de seguridad en migraciones que verifica que tu formulario de entrada tenga exactamente 8 números en el campo de pasaporte; si ponés letras, te rechaza el papel de inmediato.
*   **Enfoque PM**: Protege la base de datos corporativa contra alucinaciones o errores de formato de la IA. Es tu "Definition of Done (DoD)" a nivel de contratos de datos para la comunicación entre sistemas.

### 9. Control de Costos: Loops Infinitos (Max Iterations)
*   **Definición Técnica Simplificada**: Cortafuegos lógicos implementados por el equipo de ingeniería para prevenir que un agente entre en un bucle cerrado intentando auto-corregir un error de forma perpetua, limitando la cantidad máxima de inferencias (ej. `max_iterations = 5`).
*   **Metáfora**: Ponerle un límite máximo de gasto diario a la tarjeta de crédito corporativa para que, si el sistema de compras automáticas tiene un bug, no vacíe la cuenta bancaria de la empresa en segundos.
*   **Enfoque PM**: Evita facturas millonarias sorpresa de los proveedores cloud (OpenAI, AWS). Es imperativo exigir estos límites físicos a tu equipo técnico antes del lanzamiento a producción.

### 10. Resiliencia y Fallbacks (Rutas Alternativas)
*   **Definición Técnica Simplificada**: Planes de contingencia lógicos donde, si el sistema o la API principal que usa el agente se cae o no responde, el flujo cambia automáticamente a una ruta degradada (ej. consultar un caché local) en lugar de colapsar.
*   **Metáfora**: El generador eléctrico a gasil de un hospital que se enciende automáticamente al medio segundo de que se corta la luz de la red pública.
*   **Enfoque PM**: Asegura la continuidad operativa del negocio frente a la caída de sistemas de terceros que escapan a tu control, un escenario muy probable al orquestar docenas de agentes que dependen de APIs externas.

### 11. API Gateways (Capa de Aislamiento de Seguridad)
*   **Definición Técnica Simplificada**: Un servidor intermedio que recibe las peticiones del agente de IA, las valida, filtra e inspecciona, y recién luego las reenvía a la base de datos de producción corporativa. El agente probabilístico nunca toca los datos críticos directamente.
*   **Metáfora**: El cajero blindado de un banco. Vos le pasás el cheque por la ranura, y es el cajero (el gateway) quien saca la plata de la caja fuerte; vos jamás entrás a la bóveda.
*   **Enfoque PM**: Es la arquitectura obligatoria (Regla de Oro) a nivel Enterprise. Garantiza que ninguna alucinación o inyección maliciosa ("Prompt Injection") pueda borrar tablas (SQL Drop) o alterar registros financieros de forma directa y permanente.
