# PLIA Teams — Prototype Build Plan v2

**Date:** March 10, 2026
**Supersedes:** prototype-build-plan-8mar2026.md
**Target:** End of March (3 weeks)
**Builder:** Ruy + Claude Code
**Goal:** Clickable prototype with curated data + live AI moments for investor conversations
**Scenario:** Alfonso el Sabio — fictional iZen production

---

## 1. What We're Building

A prototype that follows the demo flow (investor-demo-flow-v2) with two surfaces:

**Google Chat** — where the AI coach lives. All individual coaching, nudges, pulse check-ins, Sara's coach conversations, and Paracaidista queries happen inside Google Chat. No new app to learn. The intelligence lives where the team already works.

**Custom Dashboard** — the only new surface. A portfolio/operational/consultant view that shows evidence alongside the coach's interpretation. Designed in Figma Make. Not a generic SaaS dashboard — a human-layer intelligence surface.

**The investor sees:**
1. A coaching nudge that arrives in Google Chat and prevents a 50K EUR crisis — 30 seconds (Beat 1)
2. An AI that answers any question about a production from a living agreement — live, in Google Chat (Beat 2b)
3. A dashboard where the coach interprets signals and invites Sara to think — evidence + interpretation side by side (Beat 6)

---

## 2. Design Principles

These emerged from the design session and govern every screen and data decision:

1. **Interpretation + evidence, side by side.** The coach interprets at the top. The evidence lives below — visual, scannable, glanceable. The user can trust the interpretation, challenge it with their own context, or ignore it and scan the evidence directly. The cognitive dissonance between interpretation and evidence is a feature — it's what makes Sara engage.

2. **Conversations, not tasks.** Signals point to conversations that need to happen, not actions to execute. "Formalizar presupuesto" is Jira. "Hay un desacople entre ambición creativa y capacidad operativa — esa conversación necesita tu peso" is PLIA. The product helps people have the right conversations at the right time.

3. **The coach initiates with a question, not a report.** "Hola Sara. Dos decisiones de alcance creativo sin respaldo de presupuesto. ¿Tú lo ves igual?" — not "Here are your 3 alerts." The question invites Sara to bring her judgment. She's the expert. The coach is a thinking partner.

4. **Trust architecture is absolute.** Sara sees consequences and patterns, never individual behavior. Pilar sees operational gaps. The consultant sees group dynamics sourced exclusively from pulse aggregates, process metrics, and operational data. Individuals own their coaching — escalation to consultant requires consent. The wall between individual and aggregate is never crossed.

5. **AI coach handles individual, consultant handles group.** Prep a hard conversation → AI coach (private, scalable). Navigate a personal pattern → AI coach. Group dynamic (us vs them, blame spiral, power imbalance in a room) → human consultant. The consultant does what the AI can't: read a room, hold tension between people, facilitate live.

6. **The product lives where the team already works.** Google Chat for all coaching. No new app, no context switch. The dashboard is the only new surface, and it serves the 3 people who need a portfolio/operational/structural view.

---

## 3. Screens

| # | Screen | Platform | Demo Beat | Mock vs Live | What It Carries |
|---|---|---|---|---|---|
| 1 | Elena's nudge | Google Chat (mock) | Beat 1 — the hook | Pre-seeded | The 30-second moment that prevents a crisis |
| 2 | Sara's coach + dashboard | Custom (Figma Make) | Beat 6 | Pre-seeded text (coach), static evidence cards | Interpretation top, evidence middle, chat bottom |
| 3 | Pilar's daily view + coach | Custom (Figma Make) | Beat 6 | Pre-seeded | Operational signals + conversation-oriented coach |
| 4 | Consultant queue | Custom (Figma Make) | Beat 6 | Pre-seeded | Group dynamics + systemic patterns |
| 5 | Paracaidista | Google Chat (mock + live AI) | Beat 2b | Live Claude API | "Ask anything about this production" |
| 6 | Coaching thread (Elena) | Google Chat (mock) | Beat 3 | Pre-seeded | 3 weeks of private exchanges — progression |

**Cut from v1:** Lucia's thread (describe verbally), Marcos's thread (describe verbally), pulse check-in screen (show aggregate on dashboard), team agreement view (Paracaidista demonstrates it's alive).

---

## 4. Dashboard Design

The dashboard is NOT a chatbot and NOT a traditional dashboard. It's both.

### Layout

```
┌─────────────────────────────────────────────────┐
│  Coach synthesis (interpretation)                │
│  "Hola Sara. Dos decisiones de alcance creativo  │
│   sin respaldo de presupuesto presionando los    │
│   mismos recursos. Pulso cayendo. ¿Tú lo ves    │
│   igual o hay algo que yo no estoy viendo?"      │
├─────────────────────────────────────────────────┤
│                                                  │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐       │
│  │Scriptorium│  │  Ecija   │  │  Pulso   │       │
│  │Sin presup.│  │+2 días   │  │  Arte    │       │
│  │5d abierto │  │Cascada   │  │ 8→5.3 ↓↓│       │
│  │2do bypass │  │Segovia   │  │ 94% cap  │       │
│  └──────────┘  └──────────┘  └──────────┘       │
│                                                  │
│  Cross-producción: bypass en 2 de 3              │
│                                                  │
├─────────────────────────────────────────────────┤
│  💬 Chat input — always available                │
└─────────────────────────────────────────────────┘
```

### Why this works

- **Reader** reads the synthesis, trusts it, moves on
- **Scanner** glances at the evidence cards, spots the pattern themselves
- **Both** reads the synthesis, checks it against the evidence, notices something the coach missed → engages in chat

Evidence cards should be **visual** — pulse as sparkline, days open as indicator, budget variance as bar. Scannable in 2 seconds without reading.

### Three altitudes, same layout

- **Sara:** portfolio view (3 productions), coach speaks strategically, "¿tú lo ves igual?"
- **Pilar:** single production, coach speaks operationally, "¿quieres verlos juntos?" / "¿por cuál empiezas?"
- **Consultant:** structural signals only, coach speaks like a colleague, "una señal estructural y una solicitud de apoyo"

---

## 5. Data Specification

### 5.1 Sara's Dashboard Signals + Coach Conversation

#### Signals

**Alfonso el Sabio — Amarillo**

Signal 1:
> "Escena 'Scriptorium / Cantigas' en calendario para martes. Sin aprobación de presupuesto. Departamento de arte al 94% de capacidad. Segundo bypass de aprobación en 3 semanas."
> *5 días abierto*

Signal 2:
> "Extensión de 2 días en Ecija no reflejada en calendario. Cascada a Segovia — permisos del castillo vencen el 15."
> *3 días abierto*

Signal 3:
> "Pulso del depto. de arte: 8.1 → 5.3 en dos semanas. 3 de 7 mencionaron 'tiempo de preparación.'"
> *En curso*

**Cacao y Compañía — Amarillo**
> "Permisos de localización: 3 días vencidos. Sin respuesta del ayuntamiento. Afecta rodaje de semana 5."
> *3 días abierto*

**CAPA Docuseries — Verde**
> "Sin señales. Último pulso: equipo en 7.8."

**Alerta cross-producción:**
> "Bypass de aprobación de escenas en 2 de 3 producciones. Patrón visto en 3 de las últimas 5 producciones de iZen."

#### Coach Conversation (3 turns)

**Coach (turn 1 — the synthesis, shown on dashboard):**
> "Hola Sara. Dos decisiones de alcance creativo entraron esta semana sin respaldo de presupuesto, y las dos presionan al mismo departamento — que lleva el pulso cayendo dos semanas. Se parece a lo que pasó en Cacao en semana 3. ¿Tú lo ves igual o hay algo que yo no estoy viendo?"

**Sara (turn 2):**
> "Sí, es parecido. Pero aquí me preocupa más porque el equipo ya está al límite."

**Coach (turn 3):**
> "De acuerdo. En Cacao se resolvió lo operativo con un gate de presupuesto en una semana. Pero lo que describes — un equipo al límite absorbiendo alcance que no se presupuestó — eso es una conversación diferente, sobre cómo se decide el alcance. ¿Quieres tenerla tú o prefieres que el consultor la facilite?"

---

### 5.2 Pilar's Daily View + Coach Conversation

#### Coach (turn 1 — synthesis):
> "Hola Pilar. Hoy tienes dos temas que se cruzan: la escena del scriptorium y la extensión de Ecija presionan el mismo calendario y al mismo equipo. Si los resuelves por separado, van a seguir chocando. ¿Quieres verlos juntos?"

#### Signals:

1. > "Escena 'Scriptorium / Cantigas' en calendario sin tu aprobación de presupuesto. Segundo caso en 3 semanas." *5d*

2. > "Extensión Ecija 2 días — no reflejada en calendario. Permisos Segovia vencen el 15." *3d*

3. > "Pulso arte: 8.1 → 5.3. Capacidad al 94%. 12 días sin descanso." *En curso*

4. > "Sync Toledo-Madrid: activo. Sin incidentes." ✓

5. > "Bypasses de aprobación: 2 en 3 semanas. Sin gate de proceso." *En curso*

#### Conversation (turns 2-3):

**Pilar (turn 2):**
> "Sí, es el mismo problema. Están entrando cosas al calendario que yo no aprobé."

**Coach (turn 3):**
> "Exacto. Hay dos conversaciones. Una rápida: establecer que nada entra al calendario sin tu firma — eso es un cambio de proceso que puedes implementar hoy. La otra es con quien está metiendo las escenas — entender por qué no está pasando por ti. Esa es más delicada porque probablemente no es intencional, es que el flujo creativo va más rápido que el operativo. ¿Por cuál empiezas?"

---

### 5.3 Coaching Threads

Private, individual, mobile (Google Chat). Each thread shows the AI coach's voice adapting to the person and the moment.

#### Elena (Production Designer) — 3 exchanges across 3 weeks

**Week 1 (onboarding check-in):**
> 🤖 "Tu equipo acordó: 'flaggear temas temprano — un problema compartido en semana 2 es una conversación, en semana 6 es una crisis.' Estás en semana 2. ¿Algo que valga la pena compartir mientras todavía es conversación?"
>
> 👤 "El research del scriptorium va más lento de lo esperado. No es crítico todavía pero si Marcos pide más escenas ahí vamos a tener un problema."

**Week 2 (pulse follow-up):**
> 🤖 "Has dicho 'con prisa' dos veces en tres semanas. ¿Qué está detrás?"
>
> 👤 "El equipo no para. Llevamos 12 días seguidos. Yo puedo aguantar pero mi equipo está llegando al límite."

**Week 3 (the nudge — Beat 1 of the demo):**
> 🤖 "Una escena nueva — 'Scriptorium / Cantigas' — apareció en el calendario del martes. No tiene aprobación de presupuesto y tu departamento está al 94%. Tu set de la biblioteca es increíble y esta escena lo lucirá — pero si el presupuesto se aprueba tarde, tu equipo no va a tener tiempo de prepararlo como tú quieres. ¿Vale la pena alinear con Pilar?"
>
> 👤 "Sí, enviar a Pilar."

#### Lucia (Director eps 5-8) — 2 exchanges

**Week 1 (onboarding):**
> 🤖 "El lunes es tu primer día dirigiendo en Alfonso. En tu onboarding describiste tu enfoque visual como 'intimidad cámara en mano' — diferente de las composiciones amplias de Javier. ¿Qué quieres establecer en la primera escena de Toledo que haga que los episodios 5-8 se sientan tuyos?"
>
> 👤 "Quiero que la cámara esté más cerca de los personajes. Que Alfonso se sienta humano, no épico. Menos planos generales, más rostros."

**Week 3 (mirror):**
> 🤖 "En las últimas dos reuniones de producción, Javier propuso el enfoque visual para locaciones compartidas y tú confirmaste sin cambios. Tu brief creativo pide intimidad cámara en mano — algo diferente. ¿Estás teniendo el espacio para desarrollar eso? El próximo rodaje en locación compartida es en 10 días."
>
> *(sin respuesta)*

#### Marcos (Showrunner) — 1 exchange

**Week 3:**
> 🤖 "La escena de las Cantigas que pediste — Elena dijo que era posible, pero no confirmó timeline ni presupuesto. Si Pilar se entera en set, puede cancelarla. ¿Quieres formalizarlo antes de que eso pase?"
>
> 👤 "Tienes razón. Le escribo a Pilar hoy."

---

### 5.4 Consultant View

The consultant sees **group dynamics and systemic patterns** only. Individual coaching is invisible unless the person consents to share. All signals trace to pulse aggregates, process metrics, or operational data — never language analysis or behavior observation.

#### Coach (greeting):
> "Dos señales estructurales esta semana en Alfonso y un patrón cross-producción."

#### Queue:

**1. Deriva entre unidades | Dinámica grupal | Alerta temprana**
> "Pulso cohesión entre unidades: 7.2 → 4.8 en dos semanas. Sync diario bajando — 5/5 semana 2, 3/5 semana 3. Tiempo de respuesta cruzado subiendo. Patrón de producciones anteriores: estos indicadores preceden ruptura de coordinación en semana 4-5. Es una dinámica de grupo — no se resuelve con coaching individual."
> *Fuente: pulso anónimo + métricas de proceso del team agreement + datos operativos PLIA*
> *Intervención sugerida: reunión conjunta de unidades. Objetivo: reconectar identidad de equipo antes de que la separación se consolide.*

**2. Bypass de aprobación — patrón sistémico | Procesos | Observar**
> "Escenas en calendario sin firma de line producer: 2 en 3 semanas (Alfonso), 1 este mes (Cacao). En 3 de 5 producciones anteriores, mismo patrón en primer mes. No es un problema de personas — es un gap en el proceso de scheduling que se repite producción tras producción."
> *Fuente: datos de scheduling tool (PLIA operativo)*
> *Intervención sugerida: proponer cambio de proceso a nivel iZen en próximo EP sync. Gate de presupuesto en scheduling tool (funcionó en Cacao).*

**3. Scriptorium — resuelto ✓**
> "Se resolvió por coaching individual. Monitorear recurrencia."

---

### 5.5 Pulse Data

#### Individual pulse (Elena — visible only to her):

| Semana | "Una palabra: ¿cómo fue esta semana?" | "¿Estás recibiendo lo que necesitas del equipo?" (1-10) | "¿Algo que hoy es conversación pero mañana podría ser crisis?" |
|---|---|---|---|
| 1 | "intensa" | 8 | — |
| 2 | "con prisa" | 6 | "El research del scriptorium va lento" |
| 3 | "con prisa" | 5 | "Mi equipo necesita un descanso" |

#### Aggregate pulse (what Sara and Pilar see — anonymous):

| Departamento | Semana 1 | Semana 2 | Semana 3 | Tendencia |
|---|---|---|---|---|
| Arte | 8.1 | 6.4 | 5.3 | ↓↓ |
| Dirección (eps 1-4) | 7.5 | 7.8 | 7.6 | → |
| Dirección (eps 5-8) | 7.0 | 6.5 | 6.2 | ↓ |
| Fotografía | 7.2 | 6.8 | 6.5 | ↓ |
| Post-producción | 7.0 | 7.0 | 6.8 | → |
| Producción (Pilar) | 6.5 | 6.0 | 5.8 | ↓ |

**Flags anónimos (semana 3):**
- 3 de 7 mencionaron "tiempo de preparación"
- 2 de 7 mencionaron "coordinación entre unidades"

---

### 5.6 Ontology Entries

Cross-production lessons that surface during onboarding and coaching. Institutional memory that currently dies when the crew disbands.

1. > "Bypass de aprobación de escenas: aparece en el primer mes en 3 de 5 producciones. El director añade escenas sin firma de line producer. En Cacao y Compañía, un gate de presupuesto en el scheduling tool lo resolvió en una semana."

2. > "Sync entre unidades en producciones de dos unidades: tiende a caer en semana 3-4. Equipos que asignaron un responsable del sync lo mantuvieron vivo. Equipos que no, reportaron ruptura de coordinación en semana 5."

3. > "Energía del departamento de arte cae cuando reciben 2+ escenas sin presupuesto en la misma semana. Precedente: 3 producciones."

4. > "Varianza de presupuesto >10% en semana 3 tiende a componer. En producciones con intervención temprana, se contuvo. En producciones sin intervención, llegó a 22% al cierre."

5. > "'Sí' que significa 'te escuché' vs 'me comprometo': aparece en todas las producciones. Causa las cascadas más caras. Equipos que distinguieron explícitamente los dos en su acuerdo tuvieron menos compromisos rotos."

6. > "Directores nuevos en setup de dos directores tienden a ceder al veterano en decisiones de estilo visual. La diferencia se nota en post-producción y es difícil de explicar sin fricción."

7. > "Emails de post-producción sin respuesta: promedio 11 días cuando no hay ruta de escalación definida. Equipos que incluyeron check-in semanal con post en su acuerdo redujeron a 2 días."

---

### 5.7 Paracaidista Context

Knowledge base the AI queries when answering live questions. Quality of answers depends on this seeded context.

#### Team Agreement (structured, per quadrant):

> **Propósito:** "Traer el mundo de Alfonso X a la vida — el rey que intentó unir tres culturas a través del conocimiento. 8 episodios que establezcan a iZen como la respuesta española al drama de época internacional."
>
> **Roles:** Marcos propone escenas. Pilar aprueba presupuesto. Director del episodio confirma calendario. Si afecta a otros departamentos, Pilar coordina. Escalación: Pilar → Sara cuando el impacto supera una producción.
>
> **Procesos:** Sync diario entre Toledo y Madrid. Urgencias por WhatsApp, día a día por email de producción. All-hands semanal. "Nada entra al calendario sin firma de line producer" (acordado semana 3 tras segundo bypass).
>
> **Relaciones:** "Flaggeamos temprano — un problema compartido en semana 2 es una conversación, en semana 6 es una crisis." "Cuando decimos 'sí,' es sí. Si no estamos seguros, decimos 'lo pienso y te confirmo.'"

#### Operational Log (what's happened since onboarding):

- Semana 1: onboarding completado. Acuerdos firmados por 7 miembros core.
- Semana 2: Elena flaggeó que research del scriptorium iba lento. Sync diario activo.
- Semana 3: Escena scriptorium entró sin presupuesto. Elena alineó con Pilar — resuelto. Extensión Ecija 2 días, cascada a Segovia pendiente. Gate de presupuesto en scheduling pendiente de implementar.

#### People Directory (roles, not behavior):

- Marcos Durán — Showrunner / Head Writer
- Pilar Ortega — Line Producer
- Javier Montero — Director eps 1-4
- Lucia Castellanos — Director eps 5-8
- Tomás Reyes — Director de Fotografía
- Elena Vidal — Production Designer
- Raúl Ibáñez — Post-producción

#### Ontology: (the 7 entries from section 5.6)

---

## 6. Trust Architecture Rules

| Persona | Sees | Never Sees |
|---|---|---|
| **Individual (Elena, Lucia, etc.)** | Their own coaching history, their own pulse trend, team agreement, ontology relevant to their role | Anyone else's coaching, anyone else's pulse |
| **Sara (EP/CEO)** | Consequences, patterns, pulse aggregates by department, cross-production alerts, process compliance metrics | Individual behavior, who caused a gap, individual coaching content, individual pulse responses |
| **Pilar (Line Producer)** | Operational gaps, pulse aggregates, process compliance, suggested conversations | Individual coaching content, individual pulse responses |
| **Consultant** | Group dynamics (from pulse aggregates + process metrics + ops data), systemic patterns, escalated requests (with individual's consent) | Individual coaching unless the person shares it, individual behavior, language analysis |

**Data source traceability — every signal must trace to one of:**
- Pulse (anonymous, aggregated)
- Process compliance (did the agreed process happen — yes/no)
- Operational system data (scheduling, budget, workload — PLIA already collects this)

**Never:**
- Language analysis ("they're saying us vs them")
- Individual behavior observation ("Marcos bypassed Pilar")
- Inference about individual state without consent

---

## 7. What's Real vs Staged

| Component | In the Demo | Notes |
|---|---|---|
| **Paracaidista** | Live Claude API with seeded context | Ask anything — unscripted |
| **Elena's nudge** | Google Chat mock with pre-seeded messages | The hook — Beat 1 |
| **Sara's dashboard + coach** | Figma Make prototype with pre-seeded text | Interpretation + evidence layout |
| **Pilar's daily view** | Figma Make prototype with pre-seeded text | Operational altitude |
| **Consultant queue** | Figma Make prototype with pre-seeded text | Structural signals |
| **Elena's coaching thread** | Google Chat mock with pre-seeded messages | 3-week progression |
| **Coaching history (Lucia, Marcos)** | Described verbally by Oseas | Cut from screens — narrative carries it |
| **Pulse check-in flow** | Not shown as screen — aggregates on dashboard | Described verbally |
| **Team agreement document** | Not shown — Paracaidista demonstrates it's alive | Described in Beat 2 |
| **Onboarding conversation** | Not shown — described in Beat 2 | Future prototype |

---

## 8. Sprint Plan

### Week 1: Data + Google Chat Mocks + Paracaidista (Mar 10-14)

| Day | What | Deliverable |
|---|---|---|
| Mon | Finalize this build plan. Set up project (Next.js for Paracaidista API). Seed all data into structured files/DB. | Data specification complete, project scaffolded |
| Tue | Build Paracaidista: API route that assembles context (agreement + ops log + ontology + directory) → Claude. | Live AI backend |
| Wed | Mock Google Chat screens: Elena's nudge (3 exchanges), Elena's Beat 1 nudge, Marcos's exchange. | 2 Google Chat mocks |
| Thu-Fri | Build + test Paracaidista chat UI (can be simple — it lives in Google Chat style). Test with 20+ questions. Tune system prompt. | Demoable AI moment |

### Week 2: Dashboards in Figma Make (Mar 17-21)

| Day | What | Deliverable |
|---|---|---|
| Mon-Tue | Design Sara's dashboard in Figma Make: coach synthesis top, 3 evidence cards (with sparklines/visual indicators), cross-production alert, chat input. Include the 3-turn coach conversation. | Sara's dashboard — clickable |
| Wed | Design Pilar's daily view: same layout, different altitude. 5 signal cards + coach conversation. | Pilar's view — clickable |
| Thu | Design consultant queue: 2 structural signals + resolved item. | Consultant view — clickable |
| Fri | Visual polish across all 3 dashboard views. Consistent design language. | 3 dashboard views polished |

### Week 3: Integration + Demo Prep (Mar 24-28)

| Day | What | Deliverable |
|---|---|---|
| Mon-Tue | Connect demo flow: transitions between Google Chat mocks and dashboard views. Build the demo "script" as a clickable path. | Connected demo flow |
| Wed | Rehearse full demo. Fix whatever breaks. Adjust data/wording based on how it flows. | Demo rehearsal #1 |
| Thu | Polish based on rehearsal. Prepare for investor-specific adjustments. | Demo-ready prototype |
| Fri | Dry run with Oseas. Final fixes. | Ready for investors |

---

## 9. Demo Script (Updated)

### Beat 1: The Hook
*Oseas shows Elena's Google Chat on screen. The nudge appears.*

> "Una escena nueva — 'Scriptorium / Cantigas' — apareció en el calendario del martes. No tiene aprobación de presupuesto y tu departamento está al 94%..."

Elena taps "Sí, enviar a Pilar." 30 seconds.

"Eso acaba de prevenir una crisis de 50K EUR. ¿Cómo lo supo el sistema? Ese es el producto."

### Beat 2: The Foundation
*Oseas describes the onboarding process — how the team agreement was created. Shows no screen — narrates.*

"Antes de empezar a rodar, el equipo se sentó y definió cómo iban a trabajar juntos. Propósito, roles, procesos, relaciones. Y no partieron de cero — el sistema les mostró lo que producciones anteriores aprendieron."

### Beat 2b: The Paracaidista
*Oseas opens the Paracaidista in Google Chat. Types a question — or lets the investor type one.*

"¿Quién aprueba cambios de escena?" → live answer from the agreement.
"¿Qué pasó con la escena del scriptorium?" → live answer from ops log + coaching.
"¿Algo de producciones anteriores que deba saber?" → live answer from ontology.

"Pregúntale lo que quieras. El AD que llega en semana 4 se orienta en 30 segundos."

### Beat 3: The Coaching Layer
*Oseas shows Elena's coaching thread — 3 weeks of exchanges on Google Chat.*

"Nadie vio esto. Privado. Siempre. El sistema se gana la confianza ayudando a las personas antes de pedirles nada."

### Beat 5: Pulse
*Oseas points to the pulse aggregates on Sara's dashboard.*

"Arte: 8 → 5 en dos semanas. Sin nombres. Sin scores individuales. 5 segundos por persona, una vez por semana."

### Beat 6: Dashboard
*Oseas opens Sara's dashboard. The coach synthesis is at the top. Evidence cards below.*

"Hola Sara. Dos decisiones de alcance creativo sin respaldo de presupuesto..." — the coach is already thinking with her.

*Clicks to Pilar's view. Then consultant's view.*

"Mismo sistema, mismos datos. Tres altitudes. Nadie recibe información que no necesita. Todos reciben la que sí."

---

## Key Risks (Updated)

| Risk | Mitigation |
|---|---|
| AI responses unpredictable in live demo | Paracaidista is the only live AI. Tune system prompt extensively. Test 20+ questions. Have 3-5 scripted questions that always work. |
| Figma Make dashboards don't look polished enough | Iterate on visual direction before building. Get one card right, then replicate. |
| Google Chat mocks look fake | Use real Google Chat interface, take screenshots, or build pixel-perfect mocks. |
| Trust architecture violations in data | Review every piece of seeded data against section 6 rules before finalizing. |
| 3 weeks isn't enough | Cut order: consultant view → Pilar's view → dashboard polish. Elena's nudge + Paracaidista + Sara's dashboard is the minimum viable demo. |

---

## Minimum Viable Demo (if time runs short)

1. **Elena's nudge** (Google Chat mock) — the hook
2. **Paracaidista** (live AI in Google Chat) — "ask anything"
3. **Sara's dashboard** (Figma Make with coach synthesis) — credibility + the coach difference

These three cover: the use case is compelling, the AI is real, and the product is fundamentally different from a dashboard.

---

## Dependencies

- Claude API key (Anthropic account)
- Figma Make access (for dashboard design)
- Google Chat interface for mocks (screenshots or pixel-perfect mockups)
- Alfonso el Sabio scenario data (this document IS the data spec)
- Demo script rehearsed with Oseas before investor meeting
- Deployment for Paracaidista (Vercel for the API, simple chat UI)

---

*Derived from: Prototype Build Plan v1 (Mar 8) + Design session (Mar 10) + Product Thesis v2-v4 + Demo Flow v2 (Mar 6) + Alfonso el Sabio scenario doc.*
