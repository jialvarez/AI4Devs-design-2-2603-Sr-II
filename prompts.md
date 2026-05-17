# PROMPTS (Cursor Pro)

# ROL Y CONTEXTO

Actúa como **Senior Product Manager + Business Analyst** con experiencia en SaaS B2B, ATS y equipos ágiles. Tu trabajo es transformar un PRD técnico en artefactos listos para desarrollo del producto **LTI** (Applicant Tracking System con IA contextual).

**Documentos fuente (léelos íntegramente antes de responder):**
- `LTI_NAR.md` — PRD: visión, KPIs, funcionalidades core, casos de uso, modelo de datos (ER), arquitectura hexagonal modular, diagramas C4, roadmap, seguridad/compliance, pricing.
- `prompts.md` — historial de prompts usados en el diseño previo (solo como contexto de tono y alcance).

**Restricciones del producto (respétalas en todas las historias y tickets):**
- Stack referenciado en el PRD: React + Tailwind (Web), API Node.js/Fastify, Workers Python, PostgreSQL 15 (JSONB), Redis, colas (Bull/Redis), S3 para CVs, integraciones OpenAI, LinkedIn, Google Calendar, HRIS.
- Arquitectura: **hexagonal modular** (monolito bien delimitado); no propongas microservicios salvo que el PRD lo justifique.
- Entidades clave del modelo: EMPRESA, RECRUITER, VACANTE, CANDIDATO, CANDIDATO_VACANTE, ENTREVISTA, PUBLICATION_CHANNEL, JOB_PUBLICATION, SUBSCRIPTION, PLAN.
- Fases del roadmap: MVP parsing (Jun 2026), APIs externas (Jul 2026), beta (Ago 2026), lanzamiento Starter (Sep 2026).
- Compliance: GDPR, RBAC (Owner > Admin > Manager > Recruiter > Viewer), auditoría de decisiones IA, encriptación de CVs.

**Idioma de salida:** español (España), tono profesional y directo.

---

# OBJETIVO DE LA ENTREGA

Genera **un único documento Markdown** llamado conceptualmente `UserStories-iniciales.md` con TODO lo siguiente en este orden exacto. No omitas secciones. No inventes funcionalidades que contradigan el PRD; si algo no está definido, márcalo como **supuesto explícito** y propón la opción más conservadora para MVP.

---

## SECCIÓN 1 — User Stories (mínimo 8, máximo 15)

Cubre al menos estos dominios del PRD (puedes agrupar o dividir según INVEST):
1. Creación de ofertas con asistencia IA
2. Publicación multicanal (LinkedIn, Indeed, etc.)
3. Recepción y parsing de CVs + scoring de match
4. Screening/revisión con IA y pipeline Kanban
5. Colaboración en tiempo real (War Room)
6. Agenda inteligente / entrevistas
7. Tests online integrados
8. Onboarding y traspaso a HRIS
9. (Opcional) Detección de sesgos / talent pool predictivo
10. (Opcional) Gestión de planes Starter/Pro/Enterprise y límites de uso

### Plantilla OBLIGATORIA (usa la misma para cada US):

```markdown
### US-XXX — [Título corto orientado a valor]

| Campo | Contenido |
|-------|-----------|
| **ID** | US-XXX |
| **Prioridad inicial** | Must / Should / Could / Won't (MoSCoW) |
| **Épica** | [nombre épica] |
| **Rol** | Como [reclutador / manager / candidato / admin...] |
| **Necesidad** | Quiero [acción observable] |
| **Beneficio** | Para [valor de negocio medible, enlazado a KPI del PRD si aplica] |
| **Descripción** | 2-4 frases de contexto de negocio |
| **Precondiciones** | Lista |
| **Postcondiciones** | Lista |
| **Criterios de aceptación** | Formato **Given / When / Then** (mínimo 5 por US, incluir happy path + al menos 2 casos borde/error) |
| **Reglas de negocio** | Numeradas (RB-01, RB-02...) |
| **Datos afectados** | Entidades/tablas del ER y campos relevantes (ej. `CANDIDATO_VACANTE.score_match`) |
| **Integraciones** | APIs/servicios externos implicados |
| **UX / Notas de interfaz** | Pantallas, estados, feedback al usuario (sin diseño pixel-perfect) |
| **No funcionales** | Seguridad, rendimiento, auditoría, GDPR si aplica |
| **Dependencias** | Otras US o infra (ej. cola de mensajes, auth JWT) |
| **Fuera de alcance** | Qué NO incluye esta US |
| **Definición de Done (DoD)** | Checklist verificable (código, tests, docs, métricas) |
| **Checklist INVEST** | Tabla Sí/No con breve justificación por criterio |
| **Story Points (Fibonacci)** | X — con 1 frase de justificación |
| **Trazabilidad PRD** | Referencia a bloque/sección de LTI_NAR.md |


## SECCIÓN 2 — Product Backlog priorizado
2.1 Metodología de priorización
Usa WSJF simplificado (Valor de negocio + Urgencia temporal + Reducción de riesgo) / Costo de desarrollo, explicando la fórmula en 5-8 líneas.

2.2 Tabla de backlog ordenada (de mayor a menor prioridad)
Rank	ID	Título	MoSCoW	WSJF (1-10)	Sprint objetivo sugerido	Dependencias	Riesgo
Alinea el orden con el Gantt/roadmap del PRD (Sprint 0 → parsing → Kanban → APIs externas → beta → Starter).

2.3 Mapa de dependencias
Incluye un diagrama Mermaid *flowchart LR* mostrando dependencias entre US.

2.4 Releases sugeridos
* Release 0 (Sprint 0): infra + auth + esqueleto
* Alpha (30 Jun 2026): ...
* Beta (15 Ago 2026): ...
* Starter (1 Sep 2026): ...

## SECCIÓN 3 — User Story elegida para descomposición
Elige una sola US de alto valor y complejidad técnica representativa (recomendación: Recepción y parsing de solicitudes con scoring, salvo que el backlog indique otra más crítica para MVP).

Indica en 3-5 líneas por qué la elegiste (impacto en KPI time-to-hire, automatización, riesgo técnico).

## SECCIÓN 4 — Tickets de trabajo (descomposición técnica para planificación)
Descompón la US elegida en tickets listos para un Sprint Planning (mínimo 10, máximo 18). Cada ticket debe ser entregable en 1-3 días por un dev.

Plantilla OBLIGATORIA por ticket:

#### TK-XXX — [Título técnico accionable]
| Campo | Contenido |
|-------|-----------|
| **Tipo** | Backend / Frontend / Worker / Infra / QA / Docs |
| **US padre** | US-XXX |
| **Descripción** | Qué se implementa y por qué |
| **Componentes** | Capa hexagonal + servicios C4 (ej. `ReceiveApplicationService`, `ResumeParsingPort`, `AIAdapter`, `MatchingEngine`) |
| **Tareas** | Checklist de subtareas concretas (mínimo 4) |
| **Contratos API** | Método, ruta, request/response JSON (esquema), códigos de error |
| **Modelo de datos** | Migraciones/tablas/campos nuevos o modificados |
| **Cola/eventos** | Nombres de colas, payloads, idempotencia |
| **Seguridad** | Auth, RBAC, encriptación, PII |
| **Pruebas** | Unitarias, integración, e2e (qué cubrir) |
| **Observabilidad** | Logs, métricas, alertas |
| **Criterios de aceptación del ticket** | Given/When/Then (mínimo 3) |
| **Dependencias** | TK-YYY |
| **Bloqueantes** | Si los hay |
| **Estimación** | Story points Fibonacci + **horas ideal** (rango) |
| **Asignación sugerida** | Rol del equipo PRD (Backend, Frontend, ML, DevOps, QA) |

Aterrizaje técnico obligatorio para la US de parsing (si es la elegida):
* Flujo async: API encola → Worker → OpenAI → persistencia → notificación.
* Manejo de errores: retry exponencial, circuit breaker, DLQ, modo degradado.
* Almacenamiento S3 + metadatos en PostgreSQL.
* Cálculo de score_match según pesos del PRD (semantic, experience, culture, potential).
* Tests: casos PDF corrupto, timeout IA, duplicado de candidato, rate limit.

## SECCIÓN 5 — Estimación de esfuerzo (Extra 🎁)
Para todos los tickets de la Sección 4:

1. Tabla resumen: Ticket | SP (Fibonacci) | Horas (min-max) | Talla camiseta (S/M/L/XL)
2. Planning Poker simulado: tabla con 5 “votos” ficticios de perfiles (Backend Sr, Backend Jr, Frontend, DevOps, QA) y consenso final.
3. Velocity asumida: 25 SP/sprint de 2 semanas → estima en qué sprint cabría la US completa.
4. Buffer de riesgo: +15% por integración OpenAI e incertidumbre de parsing.

## SECCIÓN 6 — Riesgos, supuestos y preguntas abiertas
* Lista de supuestos tomados (máx. 10).
* Lista de preguntas al PO que bloquearían refinamiento (máx. 8).
* Top 5 riesgos (técnico, legal, producto) con mitigación.

# FORMATO Y ESTILO DE RESPUESTA
* Entrega solo el contenido del .md (sin preámbulos tipo “aquí tienes”).
* Usa encabezados ## y ### consistentes.
* Tablas Markdown bien formadas.
* Diagramas solo en Mermaid cuando aporten claridad.
* No repitas párrafos enteros del PRD; referencia y operacionaliza.
* Si detectas inconsistencias en el PRD, documéntalas en la Sección 6 sin bloquear la entrega.

# CRITERIO DE ÉXITO
Un desarrollador que no haya leído el PRD debería poder, con este documento:

1. Entender qué construir en las próximas 2-3 iteraciones.
2. Refinar una US en sprint planning sin preguntas básicas de alcance.
3. Tomar un ticket TK-XXX y empezar a codear con contratos y pruebas claros.

Comienza ahora.

---

## Historial de prompts y conclusiones (entrega 17 mayo 2026)

### Prompt utilizado para generar `UserStories-iniciales.md`

Se utilizó el **prompt estructurado de este archivo** (secciones ROL, OBJETIVO, plantillas US/TK, WSJF, 6 secciones obligatorias). Entrada: lectura íntegra de `LTI_NAR.md` v2.1.

### Prompts alternativos considerados (no usados en entrega final)

| # | Enfoque | Resultado esperado |
|---|---------|-------------------|
| A | "Genera 10 user stories del PRD LTI" sin plantilla | Historias incompletas, sin GWT ni trazabilidad |
| B | Solo backlog WSJF sin tickets | Priorización útil pero sin aterrizaje técnico para devs |
| C | Prompt actual (completo) | Documento único listo para Sprint Planning |

### Conclusión: por qué el prompt completo fue el más efectivo

1. **Plantillas obligatorias** (US + TK) eliminan omisiones de RBAC, datos ER, DoD e integraciones.
2. **Orden fijo de 6 secciones** alinea entregable con rúbrica del ejercicio y roadmap Gantt del PRD.
3. **Criterio de éxito explícito** ("dev sin leer PRD puede codear") fuerza contratos API y colas en la descomposición de parsing.
4. **WSJF + Mermaid** conectan priorización con dependencias reales (auth → parsing → Kanban).
5. **Supuestos explícitos** cuando el PRD no detalla UC (War Room, HRIS) evitan inventar scope contradictorio.

**Entregable generado:** `LTI-iniciales/UserStories-iniciales.md` (11 US, backlog, 15 tickets TK-301–315 para US-003, estimación y riesgos).
