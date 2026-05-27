# Glosario Completo - Sesión 2: Inteligencia Artificial Generativa & RAG
## Conceptos Clave de Ingeniería de IA para Product Managers Estratégicos

Este glosario técnico y de negocio está estructurado para que asimiles los cimientos conceptuales de la IA Generativa, permitiéndote liderar equipos de ingeniería y defender tus decisiones de producto en entrevistas internacionales.

---

### 1. LLM (Large Language Model / Modelo de Lenguaje de Gran Escala)
*   **Definición Técnica**: Una red neuronal de aprendizaje profundo (generalmente basada en la arquitectura *Transformer*) entrenada con corpus masivos de texto para modelar la estructura probabilística del lenguaje humano. Su función principal consiste en realizar predicciones probabilísticas de la siguiente palabra o token más coherente dado un contexto previo (Next-Token Prediction).
*   **La Metáfora Cotidiana**: Es como un corrector ortográfico o un predictor de texto de celular sumamente avanzado que ha leído toda la internet pública. No "comprende" ni "sabe" nada con conciencia, simplemente sabe qué letra o sílaba debe seguir estadísticamente.
*   **Insight del Product Manager (Impacto en Negocio)**: El PM de IA debe entender el LLM como un componente de infraestructura (un motor lógico probabilístico) que se integra mediante APIs seguras. No se debe buscar que el modelo "razone" mágicamente, sino estructurar las entradas del sistema para guiar su respuesta de forma predecible.

---

### 2. Token
*   **Definición Técnica**: La unidad mínima de procesamiento lingüístico y matemático de un modelo de lenguaje. En lugar de procesar caracteres individuales o palabras enteras, los modelos segmentan el texto en fragmentos (sílabas o partes de palabras). Por regla general de la industria, **1000 tokens equivalen aproximadamente a 750 palabras**.
*   **La Metáfora Cotidiana**: Piensa en los tokens como las sílabas de un texto. Si vas a mandar un telegrama y la oficina de correos te cobra un centavo por cada sílaba leída y dos centavos por cada sílaba redactada, buscarás redactar mensajes cortos e informativos para optimizar costos.
*   **Insight del Product Manager (Impacto en Negocio)**: Toda consulta de API factura de forma variable según el volumen de tokens consumidos en el Input (Contexto) y el Output (Respuesta). El PM de IA debe auditar constantemente la cantidad de tokens por llamada para asegurar la viabilidad financiera del modelo de negocio de su producto.

---

### 3. Ventana de Contexto (Context Window)
*   **Definición Técnica**: El límite físico máximo de memoria de corto plazo que un modelo de lenguaje puede retener y procesar en una única llamada de API. Este límite incluye tanto los tokens del Prompt enviado por el usuario como los tokens de la Respuesta que el modelo debe generar.
*   **La Metáfora Cotidiana**: Es el tamaño físico de tu escritorio de trabajo. Si tu escritorio es pequeño (ventana estrecha), solo puedes trabajar con dos hojas a la vez. Si el escritorio es gigante (ventana amplia), puedes abrir un archivador completo de normativas de aduana, pero te llevará más tiempo buscar información entre tantas páginas (latencia).
*   **Insight del Product Manager (Impacto en Negocio)**: Aunque los modelos modernos ofrecen ventanas de contexto gigantescas (ej. 1 a 2 millones de tokens), saturarlas con información innecesaria eleva radicalmente el costo de la consulta y degrada el tiempo de respuesta (latencia) percibido por el usuario. El rol del PM es optimizar este espacio enviando únicamente información relevante.

---

### 4. Prompt Engineering (Ingeniería de Prompts)
*   **Definición Técnica**: La disciplina que consiste en diseñar, refinar y optimizar las estructuras de texto de entrada (instrucciones, restricciones, ejemplos de comportamiento y contexto de soporte) enviadas a un LLM para maximizar la calidad y consistencia del output generado, minimizando la variabilidad probabilística no deseada.
*   **La Metáfora Cotidiana**: Consiste en darle instrucciones sumamente detalladas y con ejemplos claros a un pasante brillante pero que no tiene contexto del negocio ni memoria de lo que hizo ayer. Si le dices "hazme un reporte", el resultado será genérico. Si le dices "hazme un reporte con esta plantilla, usando estos 3 datos y con un tono formal de 2 párrafos", el resultado será excelente.
*   **Insight del Product Manager (Impacto en Negocio)**: En el desarrollo de software corporativo, los prompts no se escriben de manera ad-hoc en un chat. Se configuran como plantillas fijas (Prompt Templates) en el backend de la aplicación, inyectando de forma automatizada las variables del usuario y aislando las reglas de negocio en la capa del sistema.

---

### 5. Embedding
*   **Definición Técnica**: Un modelo matemático que traduce palabras, oraciones o documentos de lenguaje natural a un vector numérico de alta dimensión (ej. una lista de 1536 coordenadas decimales). Este vector representa el significado conceptual o semántico del texto en un espacio geométrico de alta dimensión.
*   **La Metáfora Cotidiana**: Es como un sistema de coordenadas GPS tridimensional, pero para ideas en lugar de ubicaciones físicas. Si "puerto" y "muelle" tienen significados parecidos en logística, el modelo les asignará coordenadas geográficas extremadamente cercanas en el mapa de ideas de la computadora.
*   **Insight del Product Manager (Impacto en Negocio)**: Los embeddings permiten a nuestros sistemas buscar información basándose en el significado conceptual del texto en lugar de realizar una comparación literal por palabras clave. Esto permite que el buscador entienda consultas complejas aunque el usuario utilice sinónimos o cometa errores de ortografía.

---

### 6. Base de Datos Vectorial (Vector Database)
*   **Definición Técnica**: Un motor de base de datos especializado diseñado exclusivamente para almacenar y consultar vectores matemáticos (embeddings) de forma extremadamente veloz. Permite realizar búsquedas de similitud (como el algoritmo de K-Vecinos más Cercanos o KNN) sobre millones de vectores en milisegundos.
*   **La Metáfora Cotidiana**: Es una biblioteca gigante donde los libros no están ordenados alfabéticamente ni por código de barra clásico, sino por similitud semántica de su contenido. Los libros de exportación están en un estante junto a los manuales de logística, y muy distantes de los recetarios de cocina.
*   **Insight del Product Manager (Impacto en Negocio)**: Representa la memoria semántica persistente y segura a largo plazo para las aplicaciones de IA corporativas. Herramientas líderes de la industria como Pinecone, Chroma o PGVector son indispensables para inyectar contexto privado sin violar límites de memoria física del LLM.

---

### 7. Chunking (Fragmentación)
*   **Definición Técnica**: El proceso algorítmico de segmentar documentos de texto extensos (como PDFs aduaneros, normativas portuarias o contratos comerciales) en fragmentos o bloques discretos, uniformes y más pequeños (ej. bloques de 1000 caracteres o 250 palabras) antes de ser pasados por el modelo de embeddings.
*   **La Metáfora Cotidiana**: Consiste en cortar un libro de texto de 500 páginas en tarjetas de estudio individuales de un párrafo cada una, para que un estudiante pueda leer y asimilar rápidamente los datos específicos sin necesidad de hojear el libro completo cada vez que tiene una consulta.
*   **Insight del Product Manager (Impacto en Negocio)**: El diseño de la estrategia de Chunking (tamaño del bloque y lógica de corte por caracteres, oraciones o párrafos) determina qué tan bien la IA podrá localizar respuestas puntuales. Fragmentar de forma ineficiente fragmenta la coherencia gramatical de los datos y destruye la precisión del sistema de recuperación.

---

### 8. Overlap (Solapamiento)
*   **Definición Técnica**: La técnica de configurar un porcentaje de redundancia semántica (típicamente entre 10% y 20%) entre fragmentos (chunks) contiguos al momento de segmentar un documento extenso. Consiste en repetir las últimas palabras del Fragmento A al inicio del Fragmento B.
*   **La Metáfora Cotidiana**: Al cortar una tira de película física o realizar impresiones continuas, dejas un borde superpuesto en las uniones para asegurarte de que ninguna palabra o número importante (como una fecha o una tarifa logística) quede cortado por la mitad y pierda sentido al ser analizado por separado.
*   **Insight del Product Manager (Impacto en Negocio)**: El overlap actúa como un seguro contra la pérdida de contexto contextual. El PM debe validar con ingeniería que el solapamiento esté bien balanceado: muy poco genera respuestas incompletas, demasiado solapamiento incrementa innecesariamente los costos de consumo de tokens duplicados.

---

### 9. RAG (Retrieval-Augmented Generation / Generación Aumentada por Recuperación)
*   **Definición Técnica**: Una arquitectura de software que optimiza la calidad de las respuestas de un modelo de lenguaje. Consiste en interceptar la consulta del usuario, realizar una búsqueda semántica veloz en una base de datos vectorial para recuperar fragmentos con datos validados de negocio en tiempo real, e inyectar esta evidencia factual como contexto dentro del prompt final antes de invocar el LLM.
*   **La Metáfora Cotidiana**: En lugar de obligar a un estudiante a dar un examen de regulaciones aduaneras de memoria (entrenamiento estático del LLM), le permites rendir el examen con el libro oficial abierto sobre su escritorio (RAG), garantizando que sus respuestas se basen en regulaciones comprobables.
*   **Insight del Product Manager (Impacto en Negocio)**: Es el estándar corporativo para implementar IA generativa de forma segura y económica. Garantiza que el bot responda siempre con información autorizada, permite actualizar la base documental del negocio al instante sin re-entrenamientos costosos, y ofrece total trazabilidad de fuentes para auditorías.

---

### 10. Alucinación (Hallucination)
*   **Definición Técnica**: El fenómeno probabilístico en el cual un modelo de lenguaje genera una respuesta que es sintáctica y gramaticalmente impecable, elocuente y muy convincente, pero que es factual o lógicamente incorrecta, inventando datos, fechas, regulaciones o citas de fuentes que no existen.
*   **La Metáfora Cotidiana**: Imagina a un candidato político respondiendo una pregunta difícil en televisión con absoluta confianza, elocuencia y gesticulación perfecta, pero citando una ley inventada en el momento para no admitir que no conoce la respuesta verdadera.
*   **Insight del Product Manager (Impacto en Negocio)**: Las alucinaciones son el riesgo número uno de reputación y legalidad en soluciones de IA de cara al cliente. El PM debe liderar el diseño de mecanismos de contención (ej. RAG con umbrales de coincidencia semántica estrictos e instrucciones de sistema que prohíban al bot deducir respuestas si la base de datos documental no las contiene).

---

### 11. Golden Dataset (Conjunto de Datos de Oro)
*   **Definición Técnica**: Un conjunto curado, validado e inmutable de preguntas de usuario combinadas con sus correspondientes respuestas perfectas validadas por expertos humanos de negocio (Ground Truth). Actúa como el benchmark de referencia estándar para evaluar cuantitativamente la fidelidad y precisión del sistema de IA.
*   **La Metáfora Cotidiana**: Es la clave de respuestas oficiales de un examen de ingreso. Se utiliza para corregir los exámenes de los alumnos (evaluar nuevas versiones del bot) de forma objetiva y comparar quién obtuvo el puntaje más alto antes de liberarlos.
*   **Insight del Product Manager (Impacto en Negocio)**: Dado que la IA es probabilística, el PM no puede validar si el producto funciona bien haciendo "tres consultas de prueba" manuales en el chat. El Golden Dataset se corre de forma automatizada ante cada cambio de código en el pipeline de CI/CD para medir de forma estadística si la precisión del bot mejoró o empeoró.

---

### 12. Fine-Tuning (Ajuste Fino)
*   **Definición Técnica**: El proceso de tomar un modelo de lenguaje base previamente entrenado y continuar su entrenamiento supervisado exponiéndolo a un conjunto de datos específico de menor escala para ajustar sus pesos internos. Se utiliza para modificar su estilo de redacción, adaptarlo a una jerga técnica particular o enseñarle a seguir formatos estructurados (como JSON).
*   **La Metáfora Cotidiana**: Consiste en contratar a un abogado generalista sumamente inteligente y mandarlo a realizar un posgrado intensivo de 3 meses en regulaciones portuarias y aduaneras de Argentina para que aprenda a redactar dictámenes con la jerga y estructura formal exacta de esa especialidad.
*   **Insight del Product Manager (Impacto en Negocio)**: Un error estratégico clásico en la industria es intentar usar Fine-Tuning para enseñarle "nuevos datos factuales" a un modelo. El Fine-Tuning enseña cómo decir las cosas (formato, tono y estilo) pero no qué decir (datos fácticos dinámicos). Para incorporar conocimientos del negocio y evitar alucinaciones, la solución correcta sigue siendo RAG.
