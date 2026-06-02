# Actividad Semanal: Redacción del Mock PRD - "Cargill Customs Bot"
**Curso**: Mentoría de Posicionamiento IT / AI para Product & Project Managers
**Sesión**: Sesión 2 - IA Generativa & Arquitectura RAG
**Alumno**: Claudio Vernuccio

---

## 🎯 Objetivo de la Actividad
El objetivo de esta actividad es que asumas el rol de un **AI Product Manager** sénior en Cargill y diseñes la especificación técnica de requerimientos (PRD) de un bot inteligente de consultas aduaneras y logísticas. 

Esta planilla está diseñada para entrenar tus capacidades de especificación técnica, gobernanza y gobernabilidad de modelos probabilísticos frente a ingenieros de datos y directores de tecnología.

> [!TIP]
> **¿Querés hacerlo de forma interactiva?**
> Podés abrir el archivo [mock_prd_tarea_sesion_2.html](file:///C:/Users/franc/.gemini/antigravity/scratch/mock_prd_tarea_sesion_2.html) en tu navegador preferido. Cuenta con una interfaz interactiva premium autoevaluable con selectores dinámicos y herramientas para exportar tu PRD en Markdown o imprimirlo directamente a PDF.

---

## 🛳️ El Caso de Negocio: "Cargill Customs Bot"
### Contexto
Los despachantes de soja y agentes portuarios de Cargill en la Hidrovía Paraná-Paraguay pierden de **3 a 5 horas diarias** revisando manuales de tarifas fluviales, regulaciones del Código Aduanero e instructivos internos dispersos en PDFs pesados. Las interpretaciones incorrectas de los impuestos de flete o de las condiciones climáticas generan demoras en la salida de barcazas y multas portuarias que oscilan en miles de dólares diarios.

### Misión
Escribir la especificación (PRD) para el equipo de desarrollo, configurando un sistema **RAG (Retrieval-Augmented Generation)** sobre el modelo de lenguaje de la empresa, garantizando que el bot:
1. Responda con un tiempo de respuesta (latencia) menor a **2 segundos**.
2. **No alucine** (no invente tarifas aduaneras inexistentes).
3. Opere con absoluta **privacidad** sin fuga de datos empresariales (*Data Leakage*).

---

## 🖋️ Plantilla del PRD a Completar
*(Copiá este bloque y completalo para tu entregable)*

```markdown
# PRODUCT REQUIREMENT DOCUMENT (PRD) - CARGILL CUSTOMS BOT

**AI Product Manager**: Claudio Vernuccio
**Proyecto**: Cargill Customs Bot (Asistente RAG para la Hidrovía)
**Fecha**: [Ingresar Fecha]

---

## 1. Visión de Negocio & Alcance
### Problema
[Escribí aquí cuál es el problema operativo de los despachantes en base al caso]

### Solución Propuesta
[Explicá cómo el bot soluciona el problema usando la arquitectura RAG a libro abierto]

### Fuentes de Datos a Indexar
[Mapeá al menos 3 documentos oficiales o bases de datos internas que alimentarán al bot]

---

## 2. Ingestión de Datos & Estrategia de Chunking
*   **Algoritmo de Chunking seleccionado**: [Ej: Recursive Character Chunking / Fixed-size / Semantic]
*   **Tamaño del fragmento (Chunk Size)**: [Ej: 200 / 500 / 1000 tokens]
*   **Solapamiento (Overlap)**: [Ej: 0% / 10% / 15% / 25%]
*   **Justificación Técnica**: 
    [Explicá por qué elegiste este algoritmo, tamaño y overlap, justificando el impacto en la costura de los datos y en evitar alucinaciones]

---

## 3. Inferencia, Gobernanza y Seguridad
*   **Umbral de Confianza (Confidence Threshold)**: [Ej: 0.50 / 0.75 / 0.90]
*   **Modelo de Gobernanza (SLA)**: [Ej: Azure OpenAI Enterprise SLA (Zero-Retention) / API Pública]
*   **Filtros de Metadatos Obligatorios**: [Ej: Puerto, Año, Tipo de Documento, etc.]
*   **Estrategia contra Data Leakage**: 
    [Justificá por qué el umbral de 0.75 y las políticas contractuales del SLA de Azure OpenAI son esenciales para proteger la información comercial sensible frente a competidores]

---

## 4. Definition of Done (DoD) & Criterios de Aceptación
El desarrollo técnico del bot se considerará concluido únicamente si cumple los siguientes criterios cuantitativos:
- [ ] Umbral de confianza a 0.75 implementado en la lógica del backend.
- [ ] Overlap del 15% activo en el pipeline de ingestión vectorial.
- [ ] Conexión exclusiva a través del canal corporativo de Azure OpenAI bajo Enterprise SLA.
- [ ] Encriptación de datos TLS en tránsito y AES-256 en reposo activa.
- [ ] Metadata Filtering por Puerto y Año configurado en la base de datos vectorial (Pinecone).
- [ ] [Agregar tu propio criterio de aceptación aquí]

---

## 5. Golden Dataset de Pruebas Iniciales (Pruebas Unitarias de Regulación)
*Mínimo 5 preguntas de prueba reales basadas en el negocio, indicando la respuesta correcta oficial que el bot DEBE dar (Ground Truth).*

| ID | Pregunta del Despachante (Consulta de Test) | Respuesta Ground Truth (Respuesta Esperada Oficial) |
| :--- | :--- | :--- |
| **#1** | ¿Cuál es la tasa de peaje en la Hidrovía Paraná para barcazas nacionales? | [Respuesta esperada con fuentes oficiales y precio simulado] |
| **#2** | ¿Cómo aplica la exención del arancel para importación temporaria de Soja? | [Respuesta esperada detallando el Código Aduanero de Cargill] |
| **#3** | ¿Qué sanción aplica si un remolcador excede el tiempo límite en Puerto San Martín? | [Respuesta esperada basada en normativas internas] |
| **#4** | ¿Cuál es el procedimiento de queja ante tarifas fluviales del año 2025? | [Respuesta esperada utilizando filtros de metadatos de año] |
| **#5** | ¿Cuál es el tarifario del puerto de Paranaguá (Brasil) para esta semana? | [Indicar qué debe responder el bot si la pregunta supera el umbral y cae en no-answer] |

```
