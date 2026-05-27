# Guía de Preparación - Sesión 1: Ecosistema IT Moderno & DevOps
## Herramientas, Contenidos y Dinámica Práctica (Enfoque Re-Entry / Cargill PM)

Esta guía está diseñada para estructurar la primera sesión de manera que el estudiante experimente un "momento WOW" desde los primeros 10 minutos, sintiendo que recupera el control técnico y cierra la brecha tecnológica de forma acelerada.

---

## 🛠️ ¿Cómo usar NotebookLM para esta sesión?

**NotebookLM** es una herramienta excelente para esta fase de preparación. Se recomienda utilizar este asistente como un **"Socio de Investigación de Re-Entry"**.

### 1. Qué fuentes (inputs) cargar en NotebookLM:
Se debe crear un cuaderno nuevo en NotebookLM y cargar los siguientes elementos:
* **El CV actual del estudiante** (para que la Inteligencia Artificial comprenda su trayectoria real en Cargill y su terminología previa).
* **3 o 4 ofertas de empleo reales** de LinkedIn para puestos de *Senior Technical Project Manager IT* o *AI Product Manager* en empresas modernas.
* **Artículos de referencia sobre DevOps y CI/CD** (como la guía de CI/CD de Atlassian o AWS Fundamentals).

### 2. Qué prompts clave realizar en NotebookLM:
Una vez cargados los documentos, se deben formular las siguientes preguntas:
> * "Basado en las ofertas de empleo modernas y en el CV del estudiante, ¿cuáles son los 5 términos o conceptos técnicos en los que tiene mayor brecha (gap) y que necesita dominar en la Sesión 1 para sonar competitivo?"
> * "Genera una lista de 5 preguntas típicas de entrevista técnica para un PM en relación a metodologías de despliegue, CI/CD y branching, junto con las respuestas 'estrella' que demuestren que el candidato domina estos temas."
> * "Toma 3 logros del CV del estudiante en Cargill y redáctalos de nuevo usando terminología ágil, moderna y orientada a producto técnico (por ejemplo, reemplazando términos de gestión tradicional por sprints, despliegues continuos, APIs e integración de sistemas)."

---

## 🎨 El Recurso Visual Principal: El Pizarrón del Tiempo (Miro / Excalidraw)

En lugar de emplear diapositivas tradicionales de PowerPoint, se sugiere crear un **lienzo interactivo en Miro, FigJam o Excalidraw**. Esto proporciona una sensación de consultoría y diseño de ingeniería de alto nivel profesional.

### Estructura del pizarrón en 3 secciones horizontales:

#### 1. La Comparativa Temporal: "El Software en 2012 vs. 2026"
Dibujar dos líneas de tiempo paralelas para mostrar de forma visual el cambio de paradigma de la última década:
* **2012 (Waterfall & Monolitos)**: Servidores físicos $\rightarrow$ Base de datos única gigante $\rightarrow$ Despliegues manuales cada 3 meses en horas de la madrugada $\rightarrow$ Equipos en silos (Devs vs. QA vs. Ops).
* **2026 (Cloud Native & CI/CD)**: Microservicios en contenedores (Docker/K8s) $\rightarrow$ Servidores en la nube (AWS/Azure) $\rightarrow$ Despliegues automatizados múltiples veces al día $\rightarrow$ Cultura DevOps (automatización y monitoreo constante).

#### 2. "El Viaje de un Feature" (De Jira a Producción)
Dibujar un flujo gráfico interactivo que muestre la trayectoria de una nueva funcionalidad:
```
[Jira Ticket (PM)] 
       ⬇️
[Código Local (Dev)] 
       ⬇️
[Control de Versiones (Git Branch/PR)] 
       ⬇️
[Pruebas Automatizadas (CI - Staging)] 
       ⬇️
[Despliegue Automático (CD - Prod)]
```
*Se debe explicar en qué punto del flujo interviene el Product Manager, qué riesgos se deben mitigar en cada paso y qué preguntas clave corresponde formular en cada etapa.*

#### 3. Diccionario Visual de Traductores
Crear tarjetas de "traducción" para actualizar el vocabulario:
* ❌ *Antes se decía*: "Subir el código al servidor" $\rightarrow$  *Hoy se dice*: "Desplegar a producción (Deploy to Prod)" o "Correr el pipeline de CD".
* ❌ *Antes se decía*: "El programa que conecta las bases" $\rightarrow$  *Hoy se dice*: "El middleware" o "El servicio que expone el endpoint de la API".
* ❌ *Antes se decía*: "Hacer control de cambios" $\rightarrow$  *Hoy se dice*: "Gestionar el Git workflow mediante Pull Requests".

---

## 📝 Agenda Minuto a Minuto: Sesión 1 (60 Minutos)

| Tiempo | Bloque | Dinámica |
| :--- | :--- | :--- |
| **00:00 - 05:00** | **Check-in & Expectativas** | Rompehielos. Validar la perspectiva del estudiante frente a su reingreso al mercado IT. |
| **05:00 - 20:00** | **La Gran Actualización (2012 vs 2026)** | Recorrido visual por el pizarrón. Explicación de Monolito vs. Microservicios y APIs. |
| **20:00 - 35:00** | **El Ciclo DevOps (CI/CD)** | Explicar el "Viaje de un Feature". Mostrar cómo la automatización cambia el rol del PM (menos control manual, más gestión de métricas y calidad). |
| **35:00 - 50:00** | **Ejercicio Live: "Traducción de Experiencia"** | Tomar un proyecto real del CV (Cargill) y reescribirlo de manera conjunta en vivo usando el léxico moderno abordado. |
| **50:00 - 55:00** | **Las 3 Preguntas de Control** | Compartir las 3 preguntas exactas que se pueden formular a cualquier equipo técnico en una entrevista para sonar altamente profesional. |
| **55:00 - 60:00** | **Cierre & Tarea del Portafolio** | Explicar el entregable para la siguiente sesión y realizar la retroalimentación. |

---

## 🧠 Ejercicio Práctico Live: "Traduciendo Cargill a IT Moderno"

Tomar un logro común de gestión en una empresa tradicional y presentarlo como el resultado de la gestión de un producto tecnológico.

* **Ejemplo Tradicional**: *"Lideré la reestructuración del proceso de asignación de camiones para la carga de granos en la planta, reduciendo los tiempos de espera un 20%."*
* **Traducción IT Moderna**: *"Rol de Product Owner del sistema de optimización logística, liderando un equipo ágil e interdisciplinario. Se definió el roadmap para integrar APIs de geolocalización y bases de datos transaccionales, gestionando el ciclo de entrega mediante pipelines de CI/CD para desplegar mejoras de forma iterativa. Esto redujo la latencia operativa del proceso un 20%."*

Al observar esta transformación en vivo aplicada sobre **la propia trayectoria profesional**, se consolida la propuesta de valor del programa.

---

## 💬 Las 3 Preguntas "Rompe-Entrevistas" a dominar en esta fase

Se recomienda anotar estas preguntas. Si se formulan en una entrevista para un rol de Product Manager en IT, demostrarán de inmediato un profundo entendimiento de la ingeniería de software moderna:

1. *"¿Cómo es el Git workflow del equipo? ¿Se trabaja con GitFlow tradicional o se está implementando trunk-based development?"*
2. *"¿Qué nivel de cobertura de pruebas automatizadas se tiene en el pipeline de CI antes de fusionar (merge) una Pull Request a Staging?"*
3. *"Dado que los microservicios modernos pueden generar dependencias complejas, ¿cómo se maneja la documentación y el versionado de las APIs internas?"*
