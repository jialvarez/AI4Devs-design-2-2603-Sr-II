# Historial de prompts y conclusiones (entrega 17 mayo 2026)

## Prompt utilizado para generar `UserStories-iniciales.md`

Se utilizó el **prompt estructurado del archivo prompts.md** (secciones ROL, OBJETIVO, plantillas US/TK, WSJF, 6 secciones obligatorias). Entrada: lectura íntegra de `LTI_NAR.md` v2.1 (archivo del ejercicio anterior).

## Prompts alternativos considerados (no usados en entrega final)

| # | Enfoque | Resultado esperado |
|---|---------|-------------------|
| A | "Genera 10 user stories del PRD LTI" sin plantilla | Historias incompletas, sin GWT ni trazabilidad |
| B | Solo backlog WSJF sin tickets | Priorización útil pero sin aterrizaje técnico para devs |
| C | Prompt actual (completo) | Documento único listo para Sprint Planning |

## Conclusión: por qué el prompt completo fue el más efectivo

1. **Plantillas obligatorias** (US + TK) eliminan omisiones de RBAC, datos ER, DoD e integraciones.
2. **Orden fijo de 6 secciones** alinea entregable con rúbrica del ejercicio y roadmap Gantt del PRD.
3. **Criterio de éxito explícito** ("dev sin leer PRD puede codear") fuerza contratos API y colas en la descomposición de parsing.
4. **WSJF + Mermaid** conectan priorización con dependencias reales (auth → parsing → Kanban).
5. **Supuestos explícitos** cuando el PRD no detalla UC (War Room, HRIS) evitan inventar scope contradictorio.

**Entregable generado:** `LTI-NAR/UserStories-NAR.md` (11 US, backlog, 15 tickets TK-301–315 para US-003, estimación y riesgos).


# Instructions | EN 

In this exercise, you will act as a Product Manager and Business Analyst.

Using the documents you created in the previous section, which make up a basic PRD (key features, use cases, data model...), your task is to prepare the necessary documentation to start implementing LTI:

Generate User Stories: You can create as many as you want and can, with a minimum of 2. Use what you have learned about best practices in this chapter to ensure they contain all the necessary information. As a tip, use a common template for all of them (remember we provided a template example in the User Stories section).

Build the Product Backlog: Assemble the backlog with the User Stories, prioritizing them as you see fit according to a specific methodology. Experiment with different ways to generate a prompt that can create your backlog based on the documentation you have generated previously. Provide the different prompts you used and indicate which prompt gave you the best results. Along with the prompts, provide your conclusions on why you think this prompt was effective.

Choose a User Story: Select your preferred User Story and generate the work tickets. Detail them technically, as done in planning meetings.

(Extra 🎁) Estimate the Effort: Estimate the effort of the work tickets using the methodology (Fibonacci, Planning Poker, T-shirt sizes) and units (hours, story points) of your choice.

Use the assistant of your preference: ChatGPT, Google Gemini, Microsoft Copilot, Claude...

Don't forget to review what the assistant returns and adjust it to your needs, correcting or even removing what you deem appropriate.

Document everything in a single markdown (.md) file named UserStories-initials, and place it in the LTI-initials folder (you created it in the previous module's exercise if you submitted it) in this GitHub repository for this topic.

The repository will be collaborative, and we will be accepting pull requests to generate a common base with all folders.

Remember to update to the latest version of the repository before making your changes to avoid conflicts.

If you don't know how to stay updated before publishing your content and encounter conflicts, ask in the WhatsApp group or review documentation on Git.

Finally, don’t forget to add your prompts in prompts.md inside your folder.

Go for it!

# Instrucciones | ES


En este ejercicio vas a actuar como un Product Manager y Business Analyst. 

Usando los documentos LTI_NAR.md y prompts.md y que conforman un PRD básico (funcionalidades clave, casos de uso, modelo de datos...), tu misión es preparar la documentación necesaria para empezar a implementar LTI:

Generar las User Stories. Puedes implementar tantas como quieras y puedas, el mínimo son 2. Utiliza lo aprendido sobre buenas prácticas de este capítulo para que contenga toda la información necesaria, y como consejo, usa una plantilla común para todas ellas (recuerda que dejamos un ejemplo de plantilla en la sección de User Stories).
Arma el Backlog de producto con las User Stories, priorizándolas como consideres conveniente acorde a alguna metodología concreta. experimenta con diferentes formas de generar un prompt que te pueda genera tu back log basado en la documentación que has generado previamente. Entrega los diferentes prompts que usaste e indica cual prompt te dio mejores resultados. Entrega junto a los prompts tus conclusiones, por qué crees este prompt fue efectivo. 
Elige la User Story que prefieras, y genera los Tickets de trabajo. Aterrízalos técnicamente, tal y como se hace en las reuniones de planificación
(Extra 🎁) Estima el esfuerzo de los tickets de trabajo usando la metodología (fibonacci, poker, tallas de camiseta) y unidades (horas, puntos de historia) que prefieras.
Utiliza el asistente que prefieras: ChatGPT, Google Gemini, Microsoft Copilot, Claude...

No olvides revisar lo que te devuelve el asistente y retocarlo para adaptarlo a tus necesidades, corrigiendo o incluso borrando lo que consideres adecuado. 

Documenta todo en un único documento markdown (.md) con el nombre UserStories-iniciales, y déjalo en la carpeta LTI-iniciales (ya la creaste en el ejercicio del módulo anterior si realizaste la entrega), en este repositorio Github del actual tema.

El repositorio será colaborativo, iremos aceptando las pull requests para generar una base común con todas las carpetas. 

Recuerda actualizar a la última versión del repositorio antes de lanzar tus cambios para no tener conflictos.

Si no sabes cómo mantenerte actualizado antes de publicar tu contenido y encontrarte con conflictos, pregunta en el grupo de Whatsapp o revisa documentación sobre git.

Por último, no olvides añadir tus prompts en prompts.md dentro de tu carpeta. 


¡A por ello!
