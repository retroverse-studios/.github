# RetroVerse Studios - Strategy & Roadmap

> Created: 2026-03-17

## Vision

RetroVerse Studios makes games and tools that live at the intersection of retro aesthetics and modern AI. Every project should feel like it belongs in a world where 8-bit hardware got smarter, not just prettier.

---

## Portfolio Strategy

### Tier 1: Games (the brand)

| Project | Role | Priority |
|---------|------|----------|
| **SwipeVerse** | Flagship. Ship this first. | HIGH |
| **Incident Zero** | Only multiplayer title. Cooperative cybersecurity strategy. Tabletop + digital. | MEDIUM (tabletop ready, digital roadmap below) |
| **Stella's Evolution** | Passion project. The creative soul of the studio. | MEDIUM (design now, build after RR ships) |
| **Glomph Maze** | Retro credibility. Terminal Pac-Man fits the brand perfectly. | LOW (maintenance mode, already works) |

### Tier 2: Tools (supports the brand)

| Project | Role | Priority |
|---------|------|----------|
| **Visual Cataloguer** | "Catalog your retro collection with AI." Directly on-brand. | MEDIUM |
| **Karaoke Stage** | Entertainment. Loosely fits. Ship it, don't over-invest. | LOW (already v1.0) |

### Tier 3: Archive

| Project | Action |
|---------|--------|
| **SwipeVerse.app** | Redirect domain → retroverse.studio. Archive repo. |

---

## Roadmap

### Phase 1: Ship SwipeVerse (Now → 4-6 weeks)

The game works. The gaps are provider lock-in and the fake community store. Focus on making it releasable.

1. **Abstract AI provider** — Create provider interface, implement Gemini + Claude + OpenAI + Ollama backends. User picks in settings. This is the #1 blocker; without it, anyone without a Gemini key can't generate decks.

2. **Add deck shuffling** — Shuffle non-branching cards between plays. Small change, big replayability gain.

3. **Ship more built-in realities** — 5-8 total (currently 3). The editor exists but casual players won't create from scratch. Pre-made variety sells the concept.

4. **Harden deck generation** — Retry with backoff, validate card count, handle partial responses gracefully.

5. **Version and release** — Bump to v1.0.0, deploy to a real URL, link from retroverse.studio.

6. **Decide on community store** — Either build a minimal backend (Supabase, GitHub Gists, or static JSON repo) or remove the Store tab for v1. Don't ship fake data.

### Phase 2: Rebuild Stella's Evolution GDD (Parallel with Phase 1)

This is design work, not code. Can happen alongside SwipeVerse development.

1. **Write the Game Design Document** — 4 arcs, mechanics per arc, puzzle types, character abilities, narrative structure, visual style per era.

2. **Research Atari 2600 bankswitching** — Document the actual hardware tiers (2K, 4K, F8, F6, F4, Superchip, etc.) and map game mechanics to each.

3. **Thomas Was Alone analysis** — Study how it uses geometric shapes as characters with personality. Identify what to borrow vs. what to make unique.

4. **Prototype arc 1** — Smallest possible playable slice. Prove the "constraint as gameplay" concept works.

### Incident Zero: Tabletop → Digital Roadmap

Incident Zero is a cooperative cybersecurity board game (v2.1, feature-complete) with 6 modules, 171 cards, and d20 mechanics grounded in the MITRE ATT&CK framework. It's the studio's only multiplayer title and the only game with both a physical and digital version.

**Architecture:** One repo, two interfaces. Card definitions and rules in markdown are the single source of truth. Tabletop prints from them, digital reads from them.

```
incident-zero/
├── cards/              ← single source of truth (both versions)
├── docs/rules/         ← canonical rules (both versions implement)
├── tabletop/           ← print templates, PDF generation
└── digital/            ← web app (RetroVerse product)
```

**Phase A: Retro rebrand + tabletop polish**
- 8-bit pixel art card templates (terminal/hacker/WarGames aesthetic)
- Transfer repo to retroverse-studios org
- Print-ready PDF generation from card markdown

**Phase B: Solo digital version (AI Threat Orchestrator)**
- Web app — AI replaces the human Threat Orchestrator role
- AI generates attack chains, adapts difficulty, creates scenarios
- Single-player mode: prove the digital format works without networking
- Retro terminal UI with CRT scanlines, neon accents

**Phase C: Multiplayer digital version**
- WebSocket lobbies, real-time turns
- One player as TO (human or AI), 2-6 Blue Team defenders
- Fills the multiplayer gap in the RetroVerse portfolio
- Complements single-player titles (SwipeVerse, Stella's, Glomph)

### Phase 3: Polish & Consolidate (After RR ships)

1. **retroverse.studio** — Already refreshed. Once SwipeVerse has a URL, wire up the "Play Now" button. Add Glomph Maze as a secondary title.

2. **Visual Cataloguer web frontend** — Build the React UI. Position it as "the retro collector's tool" on the studio site.

3. **Glomph Maze** — Continue curses wrapper extraction. Consider a web-playable version (terminal.js or similar) for the studio site.

4. **Karaoke Stage** — Fix missing desktop icons. Otherwise leave it. It's done.

5. **SwipeVerse.app** — Set up domain redirect. Archive.

---

## Key Decisions Needed

1. **SwipeVerse naming/domain** — Is "SwipeVerse" too close to "Reigns"? If so, consider alternatives. Need a domain either way.

2. **Community store backend** — Build minimal backend for v1, or defer? If defer, remove the Store tab.

3. **Stella's Evolution tech stack** — Web (React/Canvas)? Native? Game engine (Godot, Phaser)? Decision should wait until the GDD is solid.

4. **Visual Cataloguer positioning** — Feature on retroverse.studio as a tool, or keep it as an independent PyPI project?

---

## Principles

- **Ship small, ship often.** SwipeVerse is playable now. Don't gold-plate it.
- **Retro is the brand, AI is the engine.** Every game should have that tension.
- **Don't maintain what you won't use.** Archive SwipeVerse. Keep the portfolio tight.
- **Document before you build.** Stella's Evolution lost its docs once. Don't repeat that.
