# PLIA Teams — Dashboard Design Spec

**Date:** March 11, 2026
**Companion to:** prototype-build-plan-v2-10mar2026.md
**Purpose:** Visual and interaction spec for the custom dashboard — the only new surface in PLIA Teams.
**Brand:** Stoic (adapted for PLIA product context)

---

## 1. Layout Decision: Hybrid

Chosen over "dashboard-first" (Option A) and "conversation-first" (Option B).

The hybrid combines a minimal portfolio status bar with a conversation-first flow. The coach's voice is the main content; evidence cards are inline artifacts the coach references.

### Page structure (top to bottom)

```
┌─────────────────────────────────────────────┐
│  ● Alfonso   ● Cacao   ● CAPA              │  ← Status bar (1-second scan)
├─────────────────────────────────────────────┤
│  Coach: "Hola Sara. Dos decisiones de       │  ← Coach synthesis (the main event)
│  alcance creativo sin respaldo de           │
│  presupuesto..."                            │
├─────────────────────────────────────────────┤
│  ┌──────────┐ ┌──────────┐ ┌──────────┐    │  ← Evidence cards (inline artifacts)
│  │Scriptorium│ │  Ecija   │ │Pulso Arte│    │
│  └──────────┘ └──────────┘ └──────────┘    │
├─────────────────────────────────────────────┤
│  Cross: bypass en 2 de 3 producciones       │  ← Cross-production alert
├─────────────────────────────────────────────┤
│  Sara: "Sí, es parecido..."                │  ← Conversation continues
│  Coach: "De acuerdo. En Cacao se resolvió…" │
├─────────────────────────────────────────────┤
│  💬 Escribe al coach...                     │  ← Chat input (always visible)
└─────────────────────────────────────────────┘
```

### Why hybrid over the alternatives

- **vs Dashboard-first (Option A):** Cards at top make the coach feel like a feature of the dashboard. Dead zone between cards and chat. Looks like every other SaaS tool.
- **vs Conversation-first (Option B):** Coach synthesis IS turn 1 of the chat — duplicating it as both a "synthesis zone" and a chat message is awkward.
- **Hybrid solves it:** Status bar gives the 1-second portfolio scan. Coach speaks immediately below. Evidence cards are "attachments" to the coach's message. Conversation flows naturally. No duplication.

### Design principle alignment

- "Interpretation + evidence, side by side" → Coach synthesis top, evidence cards below
- "Conversations, not tasks" → The page IS a conversation with data woven in
- "The coach initiates with a question, not a report" → Coach message is the main event, not the cards
- "The product lives where the team already works" → Dashboard feels like a chat, not a control panel

---

## 2. Color System (Stoic Brand → PLIA)

### From Stoic brand guide
| Token | Hex | PLIA usage |
|-------|-----|------------|
| Stoic Yellow | `#FFD500` | Warning status, capacity bars, active signals |
| Stoic Red | `#C9332B` | Urgent/critical signals, pattern badges (use sparingly) |
| Stoic Gray | `#E6E6E6` | Backgrounds, card borders, bar tracks, inactive states |
| Base White | `#FFFFFF` | Card backgrounds, page background |
| Black | `#000000` | Primary text, headings |

### PLIA-specific additions
| Token | Hex | Usage |
|-------|-----|-------|
| Status Green | `#22c55e` | Verde status — production healthy, no signals |
| Coach Purple | `#F5F0FF` (bg) / `#8b5cf6` (accent) | Coach message background tint, coach identity |
| Sara Blue | `#a5d8ff` (bg) / `#4a9eed` (accent) | User message background, chat input |
| Text Secondary | `#757575` | Labels, metadata, secondary information |
| Light Yellow Tint | `#FFF9E0` | Optional: yellow-tinted card background variant |

### Status color mapping
| Status | Left border | Dot color | Meaning |
|--------|-------------|-----------|---------|
| Amarillo | `#FFD500` | `#FFD500` | Warning — signals that need attention |
| Rojo | `#C9332B` | `#C9332B` | Urgent — escalating or time-sensitive |
| Verde | `#22c55e` | `#22c55e` | Healthy — no active signals |

---

## 3. Typography

From Stoic brand guide:

| Element | Font | Weight | Size | Color |
|---------|------|--------|------|-------|
| Card title | Montserrat Alternates | 600 (Semi-Bold) | 16-18px | `#000000` |
| Status label | Montserrat | 400 | 14px | `#757575` |
| Coach message | Montserrat | 400 | 15-16px | `#000000` |
| Metric (big number) | Montserrat Alternates | 700 | 18-20px | status color |
| Body text / details | Montserrat | 400 | 14px | `#757575` |
| Pattern badge | Montserrat | 500 | 14px | `#C9332B` |
| Chat input placeholder | Montserrat | 400 | 16px | `#757575` |

---

## 4. Evidence Card Anatomy

Each card represents one signal the coach is referencing. Cards are the evidence — the coach's message is the interpretation.

### Card template

```
┌─────────────────────────────────┐
│▌ Signal Name                    │  ← Yellow or red left border (5px)
│  Amarillo · 5d                  │  ← Status dot + days open pill
│                                 │
│  ██████████████████░░ 94%       │  ← Visual indicator (bar, sparkline, or metric)
│  Label                          │  ← What the indicator means
│                                 │
│  Core issue text                │  ← Bold, black — the "what"
│  ┌─ Pattern badge ─┐           │  ← Red border outline — the "so what"
└─────────────────────────────────┘
```

### Card dimensions
- Width: ~360px at full size, ~215px in 3-up layout (desktop ~1200px content area)
- Height: flexible, ~95-120px depending on content
- Border radius: 8px (roundness type 3)
- Border: 2px `#E6E6E6` + 5px left border in status color
- Background: `#FFFFFF`

### Visual indicator types (per signal type)

| Signal type | Indicator | Example |
|-------------|-----------|---------|
| Capacity | Horizontal bar (yellow fill on gray track) | Arte 94% |
| Pulse trend | Big metric with direction arrow or delta | 8.1 → 5.3 ↓↓ |
| Days open | Gray pill with number | 5d, 3d |
| Timeline | Text-based (deadline date) | "Permisos vencen 15" in red |
| Process compliance | Text + pattern badge | "2do bypass en 3 semanas" |
| Status OK | No card needed, or minimal green card | "Sin señales" |

### Three concrete cards (Sara's view — Alfonso el Sabio)

**Scriptorium (Amarillo)**
- Left border: `#FFD500`
- Capacity bar: 94% filled in yellow
- Issue: "Sin aprobación de presupuesto"
- Badge: "2do bypass en 3 semanas" (red outline)
- Days: 5d

**Ecija (Amarillo)**
- Left border: `#FFD500`
- No bar — text-based signal
- Lines: "+2 días extensión" / "Cascada a Segovia" / "Permisos vencen 15" (red text)
- Days: 3d

**Pulso Arte (Red border — most urgent)**
- Left border: `#C9332B`
- Big metric: "8.1 → 5.3" in red, 18px
- Lines: "94% capacidad" / "12d sin descanso" (red text)
- No days pill — ongoing

---

## 5. Status Bar

Minimal portfolio overview. One line, always at top.

```
● Alfonso    ● Cacao    ● CAPA
```

- Background: `#FFFFFF` with `#E6E6E6` border
- Height: ~35px
- Each production: colored dot (12px) + name in 14px Montserrat
- Dot color = production status (amarillo/verde/rojo)
- Clicking a production name could filter the view below (future — not in prototype)

---

## 6. Coach Message

The main content of the page. The coach speaks first.

- Background: `#F5F0FF` (light purple tint)
- Border: 1px `#E6E6E6`
- Border radius: 8px
- Label: "Coach" in `#8b5cf6`, 14px, top-left
- Text: Montserrat 400, 15-16px, `#000000`
- Full-width (spans content area)

The coach message IS turn 1 of the conversation. It's not a separate "synthesis zone" — it's the first chat bubble, just visually prominent because it's the coach.

---

## 7. Chat Behavior

### Message alignment
- **Coach messages:** Left-aligned, purple tint background (`#F5F0FF`)
- **Sara/user messages:** Right-aligned, blue tint background (`#a5d8ff`)

### Chat area
- Below the evidence cards and cross-production alert
- Shows pre-seeded conversation (Sara's reply + coach's follow-up)
- Input at bottom: white background, `#E6E6E6` border, placeholder "Escribe al coach..."
- Input always visible (sticky bottom in production; static in prototype)

### In the prototype
- Pre-seeded: 3 turns (coach, Sara, coach)
- No actual typing — it's a Figma clickthrough
- Chat area scrolls if content overflows

---

## 8. Three Altitudes (Same Layout, Different Content)

All three views use the same hybrid layout. What changes:

| Element | Sara (EP) | Pilar (Line Producer) | Consultant |
|---------|-----------|----------------------|------------|
| Status bar | 3 productions (portfolio) | 1 production (Alfonso) | 1 production (Alfonso) |
| Coach tone | Strategic — "¿Tú lo ves igual?" | Operational — "¿Por cuál empiezas?" | Peer — "una señal estructural" |
| Evidence cards | 3 cards (Scriptorium, Ecija, Pulso) | 5 cards (more operational detail) | 2 structural signals + 1 resolved |
| Cross-production | Yes — "bypass en 2 de 3" | No — single production view | Yes — systemic pattern |
| Card content | Consequences + patterns | Operational gaps + timelines | Group dynamics + source traceability |
| Never shows | Individual names, who caused what | Individual coaching content | Individual behavior, language analysis |

### Navigation between altitudes
- For prototype: separate Figma frames, click to switch
- Demo flow: Oseas clicks from Sara → Pilar → Consultant
- Future: tabs or dropdown selector at top of page

---

## 9. Cross-Production Alert

Appears between evidence cards and conversation.

- Background: `#ffc9c9` at 60% opacity (light red)
- Border: 1px `#C9332B`
- Border radius: 8px
- Height: ~30px
- Text: 14px Montserrat, `#000000`
- Only appears when there's a pattern across productions
- Sara's view: "Bypass de aprobación en 2 de 3 producciones"
- Consultant's view: elevated to a full signal card (systemic pattern)

---

## 10. Visual References

Screenshots saved in `references/` folder:

| Product | Pattern | File prefix | Key takeaway |
|---------|---------|-------------|-------------|
| Perplexity | Chat-first + inline citations | `perplexity-*` | Coach synthesis = Perplexity answer. Evidence cards = citation chips. |
| Accern Rhea | Split-screen chat + report | `accern-rhea-*` | Power-user pattern. Relevant for consultant view. |
| Hex Threads | Chat → inline data viz | `hex-threads-*` | Question triggers data. Chat IS the analytics surface. |
| Cleo AI | Pure chat-first finance | `cleo-*` | Data cards inside conversation stream. Mobile-first. |
| Lazarev article | AI dashboard principles | `lazarev-*` | 5 principles: hierarchy over density, citations with outputs. |

### Wireframes
- **Layout comparison (Option A vs Hybrid):** [Excalidraw link](https://excalidraw.com/#json=_01jFWDyj5DIS9CV3r-Am,dqfeECqWYMP3OIUirR5ULg)
- **Evidence card + hybrid context (Stoic brand):** [Excalidraw link](https://excalidraw.com/#json=LeUstek1ZDK2JJokICpFL,ZsDnlV7kqoDKOBelZ4g6cw)

---

## 11. Open Questions

- [ ] Green for "Verde" status — `#22c55e` works but isn't in Stoic palette. Confirm or pick a Stoic-compatible green.
- [ ] Card interaction in prototype — do cards expand on click? Or are they static?
- [ ] Coach avatar/icon — does the coach have a visual identity (icon, avatar) or just the "Coach" label?
- [ ] Suggested prompts — does the chat input show suggestion chips (like Perplexity) or just a blank field?
- [ ] Mobile responsiveness — prototype is desktop-first, but does the demo ever show mobile? (Google Chat mocks are mobile-like)
- [ ] Pulse sparkline — should Pulso Arte card have a mini sparkline showing the 3-week trend, or is the big metric "8.1→5.3" enough?

---

*Derived from: Design session (Mar 11, 2026) + Prototype Build Plan v2 + Stoic Brand Guidelines + Visual reference research.*
