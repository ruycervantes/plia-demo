# V0 Technical Spec — For Mike

**Target:** Friday March 21, 2026

---

## What Mike needs to do

**Give Ruy SSH access to the Vultr server with his keys.** Ruy does the rest directly in OpenClaw.

---

## What Ruy builds in OpenClaw

### Files (the Telos — flat Markdown)

| File | Content | Who creates |
|------|---------|-------------|
| `telos-team.md` | Purpose, goals, challenges of the team | Ruy (from AI interviews + hackathon) |
| `telos-company.md` | Strategic chain: Axialent, Stoic, PLIA, what we're testing | Ruy |
| `telos-members.md` | Each member: role, goals, challenges | Ruy (AI interviews each person) |
| `transcripts/` | Meeting transcripts, uploaded manually | Whoever convened the meeting |

### Skills (3 total)

**1. `/analyze` — Meeting analysis**
- Reads: transcript + all Telos files
- Lenses: Katzenbach (Purpose, Roles, Relationships, Processes)
- Outputs: 2 content observations + 2 performance observations (individual + team)
- Rule: "I noticed" language, never "this happened" or "decided"
- Rule: every observation must reference a Telos goal/challenge — no generic insights

**2. `/fifth-member` — Mentor perspective**
- Reads: transcript + all Telos files + output from `/analyze`
- Persona: startup mentor (Paul Graham initially, swappable)
- Outputs: 1 perspective that counterweights what the team needs
- If we're over-analyzing → pushes action. If we're rushing → pulls back.

**3. `/correct` — Correction handler**
- Triggered by: Telegram reply ("that wasn't a decision, just an idea" / "wrong, what actually happened is X")
- Does: updates the relevant Telos file or adds a note to the transcript context
- Confirms back: "Updated. Next analysis will reflect this."

### Workflow (post-meeting)

```
Ruy uploads transcript to transcripts/
        ↓
  /analyze (reads transcript + Telos)
        ↓
  /fifth-member (reads transcript + Telos + analysis)
        ↓
  Format as digest → send to Telegram group
        ↓
  Members reply with corrections → /correct updates files
```

---

## Context source material

Ruy will process and distill the Telos files from the Axialent/Stoic content pack (`inbox/ax y stoic content CONFIDENTIAL/`):

- `01_AXIALENT_OVERVIEW.md` — company context
- `02_CONSCIOUS_BUSINESS_FRAMEWORK.md` — methodology
- `03_AXIALENT_OFFERING.md` — what Axialent does
- `04_STOIC_OVERVIEW.md` — Stoic context
- `05_MARKET_AND_COMPETITIVE.md` — market positioning
- `06_STOIC_PRODUCT_VISION.md` — product direction
- `07_ANALYSIS_FRAMEWORKS.md` — analytical lenses
- `08_TEAM_PAI_ARCHITECTURE.md` — team AI architecture

These get distilled into the 3 Telos files above — not uploaded raw. The agent needs curated context, not a document dump.

## Onboarding flow

Once Ruy has the draft Telos files, each team member does a short AI-guided conversation (via Telegram or OpenClaw chat):

**Step 1: Validate the team Telos (~5 min)**
The agent shows the team purpose, goals, and challenges and asks: "Does this match your understanding? What's missing or wrong?" Each member's corrections refine the shared Telos before any analysis runs.

**Step 2: Individual interview (~10 min)**
The agent asks each member:
- What's your role on this team? What are you responsible for?
- What are your personal goals for this work?
- What's the biggest challenge or risk you see right now?
- When the team isn't working well, what does it look like?

Their answers populate `telos-members.md` — the individual layer of context.

**This is also the first product experience.** The onboarding IS the prototype of the team agreement process from the thesis. If the team finds the conversation valuable, that's signal. If it feels like a chore, that's signal too.

---

## Blocker

- [ ] Mike: add Ruy's SSH keys to Vultr server

Once that's done, Ruy can start building the skills and Telos files directly.
