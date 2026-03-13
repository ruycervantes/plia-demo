# PLIA Data Infrastructure — Context for PLIA Teams

**Date:** March 5, 2026
**Purpose:** Document what PLIA already captures and how PLIA Teams **could** leverage the same data pipes for the human layer.
**Status:** PLIA Teams does not exist yet. Everything about PLIA Teams in this doc is speculation / vision — what the product could do if built.

---

## What PLIA Is

PLIA is an AI-native operating system that structures, standardizes and automates every stage of audiovisual production — from script to screen. Built on 40+ years of hands-on production expertise (Jose Velasco's career at iZen).

- **Company:** 2-10 employees, founded by Jose Velasco and Laura Arranz Fernandez
- **Status:** Active development and internal testing (as of 2026)
- **Clients:** Prime Video, TF1, Paramount+
- **Parent:** iZen group (Zebra Producciones, Newco, CAPA, etc.)

### Four Solution Pillars (all operational)

1. **IP & Story Management** — script tracking, IP pipeline
2. **Smart Pre-production** — script breakdown, scheduling, budgeting
3. **Real-time Production** — on-set operations, live tracking
4. **Advanced Post-production** — VFX, editing, delivery workflows

### The Problems PLIA Solves (from their website)

- **Fragmented workflows:** Scripts, budgets, schedules scattered across tools and teams. No single source of truth.
- **Costly late-stage changes:** Budget overruns. Missed deadlines. Decisions that cost millions arrive too late.
- **Zero visibility:** No end-to-end visibility. Key decisions made in the dark without data.
- **Administrative extraction:** Creative teams waste hundreds of hours on tedious administrative work. Not the exception — the rule.

---

## PLIA's Data Sources

### 1. Scripts — via Final Draft + Movie Magic

**Final Draft** is the industry standard for screenwriting (95% of the entertainment industry). Scripts flow from Final Draft into production management tools.

**Movie Magic** (by Entertainment Partners) dominates production management:
- **Movie Magic Budgeting** — industry standard for film/TV budgeting. Handles multi-currency, tax incentives, episodic budgeting.
- **Movie Magic Scheduling** — industry standard for scheduling. Multi-unit, multi-episode, conflict detection, drag-and-drop.

The production stack:
```
Final Draft (script writing)
    → Script breakdown (scenes, locations, cast, props, VFX, stunts)
    → Movie Magic Scheduling (breakdown → shooting schedule)
    → Movie Magic Budgeting (breakdown → budget by department)
```

PLIA ingests this data. From the script, PLIA's agents can identify product placement opportunities, flag VFX-heavy scenes, estimate department workloads, and catch scheduling conflicts before they cascade.

### 2. Communications — via Google Chat

iZen's production teams communicate through Google Chat. PLIA's agents listen to these conversations to catch operational signals — missed orders, logistics issues, coordination gaps.

This is where most "verbal" commitments actually live. What looks like on-set verbal communication often has a text trail in group chats:
- "Necesitamos 2 dias mas en Ecija"
- "Ya hable con Elena y dice que puede adaptar el set"
- "El plano secuencia no esta saliendo con la luz de la tarde"

The same chat stream that PLIA reads for operational intelligence, PLIA Teams reads for human dynamics — commitments, misalignments, assumptions.

### 3. Budgets and Schedules — structured operational data

PLIA tracks budget actuals against plan, schedule adherence, resource allocation. This gives the system real-time knowledge of:
- Which scenes are over/under budget
- Which departments are stretched
- Where schedule pressure is highest
- What the cascade impact of a change would be

---

## What PLIA Teams Could Add — The Human Layer (VISION — product does not exist yet)

PLIA sees the operational layer. The hypothesis: same data, different lens.

| Data source | What PLIA sees (operational) | What PLIA Teams sees (human) |
|---|---|---|
| Script breakdown | Product placement opportunities, VFX complexity, budget line items | Which scenes are high-stakes for commitments (battles = schedule-sensitive, complex setups = cross-department coordination) |
| Google Chat | Missed orders, logistics gaps, operational coordination | Commitments made, assumptions not validated, misalignment between what A said and what B understood |
| Schedule | Timeline adherence, conflict detection | Cascade impact of verbal decisions ("2 extra days" = which downstream commitments break?) |
| Budget | Spend vs plan, department variances | Unbudgeted scope creep driven by creative ambition (Marcos → Elena scriptorium scene) |

### The Key Hypothesis

If PLIA has already solved the data capture problem — agents reading scripts, listening to chats, tracking budgets and schedules — then PLIA Teams wouldn't need to build new capture infrastructure. It would read the same data through a different lens.

The same Google Chat message where PLIA's agent catches "this order needs to go out today" could be where PLIA Teams catches "Marcos just told Elena to build a new set and nobody told Pilar."

The same script breakdown where PLIA calculates VFX budget could be where PLIA Teams understands that commitments around the battle of Ecija are high-stakes because Movie Magic shows 3 downstream schedule dependencies.

*This is the vision. Whether PLIA's data pipes are actually accessible and structured in a way that supports this is an open question that needs validation with Velasco/Oseas.*

### What Would Make Commitment Extraction Intelligent (not dumb pattern matching)

Without PLIA's data:
- "Necesitamos 2 dias mas" = generic schedule request
- AI extracts it as an action item. That's it.

With PLIA's data (hypothetical):
- "Necesitamos 2 dias mas en Ecija" + Movie Magic shows Segovia depends on Ecija completion + budget shows location permits expire on the 15th + the scene is the battle sequence (script breakdown: 300 extras, stunts, horses)
- AI would know this is a 200K EUR cascade risk that affects 3 departments and 2 locations
- The nudge to Javier wouldn't be "you have a pending action item" — it would be "tu plano secuencia queda perfecto pero pierdes la locacion de la corte"

**The thesis: context makes the AI useful. PLIA could provide the context. PLIA Teams would provide the human intelligence on top. Whether this integration is feasible is unvalidated.**

---

## What PLIA Likely Does During Production (SPECULATION — needs confirmation)

PLIA's website lists "Real-time Production" as a pillar but gives no detail. Based on what we know (agents listening to Google Chat, script/budget/schedule data), here's what's plausible:

**Probable capabilities during production:**

1. **Product placement tracking** — script says "character drinks coffee in scene 14." Agent ensures the brand's product is on set, captured on camera, logged for billing. Miss a placement = miss revenue.
2. **Order/logistics coordination** — "we need 300 extras for the battle on Thursday." Agent tracks whether casting call went out, transport booked, costumes ready. Miss an order = production stall.
3. **Schedule adherence** — comparing what was shot today against what Movie Magic planned. If unit A is behind, what's the downstream effect on unit B?
4. **Budget tracking** — real-time spend vs plan. When art department orders materials for a new set, does it match a budgeted line item or is it unplanned?
5. **Continuity/documentation** — ensuring DIT backs up footage, slates are logged, VFX plates tagged correctly.

**What PLIA probably does NOT do (= the PLIA Teams gap):**

- Doesn't know that Javier's "si" to Tomas was a technical opinion, not a schedule commitment
- Doesn't know that Elena said "possible" not "confirmed"
- Doesn't track whether team operating agreements are being honored
- Doesn't detect that two units are drifting into "us vs them"
- Doesn't notice that Lucia agreed out of deference, not conviction
- Doesn't surface that Raul's email with 6 issues went unread for 2 weeks

**The gap is the human interpretation layer.** PLIA knows the order went out. It doesn't know that the conversation behind the order had three people understanding three different things.

*This section is speculation based on inference from PLIA's website, known data sources (Google Chat, scripts, budgets), and production industry patterns. Needs confirmation from Oseas or Velasco before the demo relies on any of this.*

---

## The Ontology Foundation (VISION — how it could work)

If PLIA's data is accessible, it would become the first layer of the organizational ontology:

1. **Script/production structure** — what scenes exist, what departments are involved, what the schedule looks like. This is the "world" the team operates in.

2. **Communication patterns** — who talks to whom, through what channels, how decisions get communicated. From Google Chat history, the system learns that Marcos tends to go direct to department heads, that Pilar is always the bottleneck, that Raul's emails go unread.

3. **Team onboarding** (PLIA Teams adds this) — the team's own agreements, roles, purpose, operating principles. This is what the system measures against.

4. **Behavioral data** (PLIA Teams adds this over time) — commitment patterns, misalignment frequency, which agreements hold and which break. Compounds across productions.

```
Layer 1: PLIA operational data (scripts, budgets, schedules, chat)
    ↓ already captured
Layer 2: PLIA Teams context (team agreements, roles, purpose)
    ↓ captured at onboarding
Layer 3: PLIA Teams behavioral data (commitments, misalignments, patterns)
    ↓ compounds over time
Layer 4: Cross-production organizational knowledge
    ↓ the moat — nobody else has this
```

---

## Implications for the Demo

1. **Assume the data is already flowing.** For demo purposes, we present as if PLIA's data pipes are available. The demo starts from "the data exists" and shows what a human-layer product would do with it. Whether the integration is real is a separate validation step.

2. **The commitment extraction story is stronger with context.** When the demo shows the AI extracting commitments, the pitch is that it's not generic NLP — it's an AI that could know the script, the schedule, the budget, and the team agreements. That's the aspirational product, not current reality.

3. **The PLIA + PLIA Teams story for investors:** "PLIA solved the operational layer — scripts, budgets, schedules, logistics. Same data pipes. PLIA Teams would add the human layer — who committed to what, where are they misaligned, which agreements are breaking. Together: end-to-end production intelligence."

4. **The moat thesis:** PLIA's operational data gets richer over productions. PLIA Teams' behavioral data would get richer over productions. A production company using both across 10 crews would build organizational intelligence that no competitor can replicate. This is the vision — not yet proven.

### Open Questions (must validate before building)

- Can we actually access PLIA's data? What APIs, formats, permissions exist?
- Does PLIA use Final Draft / Movie Magic or something else? (Assumed, not confirmed.)
- Is Google Chat the actual communication channel for all productions?
- How much of PLIA's "80-100 agents" is real vs aspirational?
- Would Velasco grant PLIA Teams access to PLIA's data layer, or are these truly separate products?

---

## Context Sources Are Pluggable — Production Is the First Vertical

The architecture isn't "we read PLIA's data." It's: **every industry where teams coordinate complex work already has structured artifacts that describe the work. PLIA Teams reads those artifacts as context.**

| Vertical | "Script" equivalent | "Breakdown/Schedule" equivalent | "Budget" equivalent | "Chat" equivalent |
|---|---|---|---|---|
| Film production | Final Draft (scripts) | Movie Magic Scheduling | Movie Magic Budgeting | Google Chat |
| Software development | PRDs / product specs | Jira / Linear / Asana | Resource allocation / roadmaps | Slack / Teams |
| Consulting | SOWs / project scopes | Deliverable trackers | Time tracking / budgets | Email / Teams |
| Construction | Blueprints / plans | Project schedules (Primavera, MS Project) | Cost estimates | Field communication apps |

The pattern is identical: **structured work artifacts + unstructured communication.** The work artifacts give context. The communication is where commitments are made, broken, and misunderstood.

**For the demo:** Production is the concrete scenario. Alfonso el Sabio makes it real for the PLIA investor. But the end-of-demo slide should make the investor see: this works anywhere teams coordinate complex work. Production is where we start — not where we stop.

**For the architecture:** PLIA is a context source, not the platform. PLIA Teams connects to PLIA the same way it would connect to Jira or GitHub. This aligns with Oseas's negotiation condition: "product can be standalone, not locked to PLIA platform."

---

## Competitive Landscape (production tools)

| Tool | What it does | Gap PLIA Teams fills |
|---|---|---|
| Final Draft | Script writing (industry standard, 95% market) | No production management, no team layer |
| Movie Magic Scheduling | Scheduling, conflict detection | No commitment tracking, no human dynamics |
| Movie Magic Budgeting | Budget management, cost estimation | No visibility into why budgets overrun (human causes) |
| StudioBinder | Cloud-based breakdown, scheduling, call sheets | Modern but operational only — no team health |
| Filmustage | AI script breakdown, scheduling | Pre-production focused, no on-set or team layer |
| Scriptation | Script annotation, paperless on-set | Individual tool, no team coordination |
| PLIA | End-to-end operational automation (script to screen) | Operational only — no human/team layer |
| **PLIA Teams** | **Human layer on top of PLIA's operational data** | **The missing piece — commitments, alignment, team health** |

No tool in the market addresses the human coordination layer in production. They all optimize the operational side (scripts, budgets, schedules). Nobody helps the 200+ people on a production actually stay aligned with each other.

---

*Sources:*
- [PLIA website](https://www.plia.ai/)
- [PLIA LinkedIn](https://www.linkedin.com/company/plia-ai)
- [Movie Magic Scheduling — Entertainment Partners](https://www.ep.com/movie-magic-scheduling/)
- [Movie Magic Budgeting — Entertainment Partners](https://www.ep.com/movie-magic-budgeting/)
- [Final Draft — industry standard](https://www.finaldraft.com/)
- [StudioBinder — script breakdown](https://www.studiobinder.com/script-breakdown-software/)
- [Filmustage — AI pre-production](https://filmustage.com/)
- [iZen company structure — C21 Media](https://www.c21media.net/inside-izens-global-ambition-under-ceo-sara-fernandez-velasco/)
