# RetroVerse Studios - Portfolio & State of Play

> Last updated: 2026-03-17

## Studio Identity

**RetroVerse Studios** is an independent game studio based in Perth, Australia.
Tagline: *"Where Classic Pixels Meet Next-Gen Choices"*

- Website: [retroverse.studio](https://retroverse.studio)
- Focus: Retro-pixel aesthetics fused with modern AI-driven decision mechanics

---

## Active Projects

### 1. SwipeVerse (Flagship)

**What:** Card-based survival strategy game. Swipe left/right to make decisions that affect 4 stats across themed realities. AI generates dynamic narratives.

**Tech:** React 19 + TypeScript, Vite, Google Gemini API, React Flow, PWA

**Status:** Playable, feature-rich, pre-release (v0.0.0)

**What works:**
- Full gameplay loop (swipe cards, manage stats, win/lose conditions)
- 3 built-in realities: Cyberpunk Dystopia, Mystical Kingdom, Galactic Imperium
- Reality Editor with AI deck generation, JSON import, and manual card creation
- Visual graph editor for branching narratives (React Flow)
- PWA with offline support and installable
- Sound system (base64-encoded WAV)
- localStorage persistence

**What's incomplete:**
- AI is hardcoded to Gemini only (no provider abstraction)
- Community Store is 100% mock data (no backend)
- Stats hardcoded to Power/Wealth/People/Knowledge internally (custom names are cosmetic)
- No deck shuffling or randomization between playthroughs
- No retry logic for failed AI generation
- No versioning (still v0.0.0)

**Key files:**
- `App.tsx` - Main orchestrator (269 lines)
- `components/GameScreen.tsx` - Gameplay loop (340 lines)
- `components/EditorScreen.tsx` - Reality editor (541 lines)
- `services/geminiService.ts` - AI deck generation (Gemini only)
- `services/apiService.ts` - Mock community store
- `constants.tsx` - Built-in realities

---

### 2. Stella's Evolution (In Concept)

**What:** A four-arc puzzle game paying homage to the Atari 2600's hardware evolution. Geometric AI beings (inspired by *Thomas Was Alone*) solve puzzles through increasingly complex realities — from 2K simplicity to bankswitched brilliance.

**Theme:** "Chase the beam" — referencing the Atari 2600 TIA chip's real-time scanline rendering.

**Structure:** 4 arcs mapped to Atari 2600 RAM/bankswitching tiers:
- Arc 1: 2K/4K era — minimal resources, pure constraint
- Arc 2: 8K F8 bankswitching — expanded possibility
- Arc 3: 16K F6 — complexity emerges
- Arc 4: Superchip/extended — full capability unlocked

**Status:** Concept only. Original design documentation was lost. Core idea preserved, needs full GDD rebuild.

**Tech:** TBD (likely web-based given studio's stack)

---

### 3. Glomph Maze

**What:** Modernized fork of MyMan — a text-based terminal Pac-Man clone in C.

**Tech:** C17, CMake, ncurses, optional SDL2 audio

**Status:** Excellent condition. Builds cleanly, 4/4 tests passing.

**What works:**
- 4 size variants (standard, xlarge, small, tiny)
- 480+ mazes, 91 tilesets, 73 sprite sets, 20+ MIDI sound files
- Modularized from monolithic 6K-line file into 9 focused modules
- Full input support (arrows, HJKL, numpad, Emacs bindings)
- Color, pause, help system all working

**What's left:**
- Extract curses wrappers (~800 lines, planned next step)
- Minor memory leaks in file parsers
- SPRITE_REGISTERS macro warning (harmless)
- Runtime maze switching and save/load (future features)

**Key files:**
- `src/myman.c` - Core game loop (5,224 lines)
- `src/logic.c` - AI and game rules
- `CMakeLists.txt` - Build configuration
- `docs/REFACTORING_STATUS.md` - Detailed roadmap

---

### 4. Karaoke Stage

**What:** Modern themed karaoke player supporting CDG+MP3 and LRC lyric formats, with pitch detection and singing scores.

**Tech:** React 19 + TypeScript, Vite, Electron 39, cdgraphics, Web Audio API, IndexedDB

**Status:** Production-ready (v1.0.0). Desktop builds completed Dec 2025.

**What works:**
- CDG and LRC format playback
- Song library management (IndexedDB, no server needed)
- 8 pre-built themes + custom category creation
- Auto-categorization via keyword matching
- Real-time pitch detection with autocorrelation algorithm
- Singing score system (percentage, 5-star rating, streak tracking)
- Electron desktop builds (macOS x64/arm64, Windows, Linux)
- Dark/light mode, responsive design
- Folder bulk import with auto-pairing

**What's incomplete:**
- Missing icon assets for desktop builds
- One TODO: library refresh after bulk import (forces page reload)
- Docker and Tauri builds planned but not implemented
- No video features yet (camera permission configured but unused)

**Key files:**
- `App.tsx` - Root component
- `components/KaraokeStage.tsx` - Main player
- `components/PitchMeter.tsx` - Real-time pitch feedback
- `formats/CdgRenderer.ts` - CDG graphics playback
- `electron/main.cjs` - Desktop app entry

---

### 5. Visual Cataloguer

**What:** Batch cataloguing tool for physical collections (retro games, books, vinyl, etc.) using QR code dividers and AI-powered image recognition.

**Tech:** Python 3.11+, OpenCV, Tesseract OCR, Anthropic Claude API, Ollama, FastAPI, SQLite

**Status:** Alpha (v0.8.0). Published on PyPI. Actively developed.

**What works:**
- Full pipeline: scan images → detect dividers → AI identify items → store in DB
- Claude and Ollama AI providers with auto-detection
- QR code + OCR divider detection (printed and handwritten)
- RAW file support (14+ camera formats)
- Multi-camera merge by EXIF timestamp
- Resume capability with SHA256 deduplication
- 11 CLI commands (process, list, search, edit, review, export, serve, etc.)
- REST API via FastAPI
- CSV/JSON export
- 1,580 lines of tests, strict mypy

**What's incomplete:**
- React frontend not built (web interface is placeholder HTML)
- No batch re-identification
- No perceptual hash deduplication (schema field exists, unused)
- No eBay listing generation (tracking fields exist)
- No API authentication

**Key files:**
- `cataloguer/processor/pipeline.py` - Main orchestration
- `cataloguer/processor/identifier.py` - AI providers
- `cataloguer/cli.py` - Full CLI (1,024 lines)
- `cataloguer/api/app.py` - FastAPI setup

---

### 6. Incident Zero

**What:** Cooperative cybersecurity strategy board game. One player acts as Threat Orchestrator (attacker), 2-6 others form Blue Teams (defenders). Uses d20 mechanics grounded in the MITRE ATT&CK framework. Available as printable tabletop game with a digital edition planned.

**Tech:** Markdown (card/rule definitions), Web (digital edition planned)

**Status:** Feature-complete MVP (v2.1). 6 modules, 171 cards. Not yet playtested with real players.

**What works:**
- 6 interchangeable modules: Network Building, Hardening, Incident Response, Disaster Recovery, Forensics, Audit & Compliance
- 171 cards across all modules (threat, defense, investigation, evidence, crisis, audit)
- Variable game length system (30-55 min per module)
- Modules chain together with outcome modifiers (play any sequence)
- Complete documentation (15,600+ lines)
- Contribution framework and scenario design templates

**What's incomplete:**
- No real-world playtesting yet (highest priority)
- Card balance unvalidated
- No digital version (roadmap in FUTURE_WORK.md: Phase A retro rebrand, Phase B solo AI mode, Phase C multiplayer)
- No print-ready PDF generation
- No database system (cards in markdown)

**Key files:**
- `cards/` - All card definitions by module
- `docs/rules/` - Full rules for each module
- `docs/FRAMEWORK.md` - Module design philosophy
- `FUTURE_WORK.md` - 15-item roadmap + digital edition phases

**Portfolio role:** Only multiplayer title. Contrasts with single-player SwipeVerse, Stella's Evolution, and Glomph Maze.

---

## Archived / To Retire

### SwipeVerse.app

**What:** Landing page for SwipeVerse — updated to reflect the new game (cyberpunk/mystical/galactic realities, AI features).

**Status:** Promo site with "Play Now" CTA. No game code — links to deployed game.

---

## Moved Out of RetroVerse

- **lane-read** — Bowling shot tracker → independent project (laneread.com)
- **virtual-lanes** — Bowling simulation library → independent project (PyPI)

---

## Infrastructure

| Asset | Status | Notes |
|-------|--------|-------|
| retroverse.studio domain | Active | Main website, vanilla HTML/CSS/JS |
| swipeverse.app domain | Active | Should redirect to retroverse.studio |
| retroverse.studio email | Active | michael@retroverse.studio (newsletter) |
| GitHub org | retroverse-studios | Hosts repos |
| PyPI | visual-cataloguer published | v0.8.0 |
