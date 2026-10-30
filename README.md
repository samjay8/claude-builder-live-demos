# Live Demos — Built with AI in 15 Minutes

Three tiny, dependency-free demos built live as a demonstration of what AI can help you ship in a single sitting: an OOP teaching tool, a creative AI toy, and a room-wide interactive wall.

**Everything here is plain HTML/CSS/JS.** No frameworks, no build step, no API keys. Clone it, fork it, open a file — it just runs.

## 🔗 Try it live

All three demos are deployed on GitHub Pages:

**https://samjay8.github.io/claude-builder-live-demos/**

## The three demos

| # | File | What it does |
|---|------|--------------|
| 01 | `flashcard-quiz.html` | **OOP Flashcard Quiz** — 8 flashcards on Encapsulation, Abstraction, Inheritance & Polymorphism. Multiple choice, keeps score and misses, explains every answer, grades you at the end, retry for a new run. |
| 02 | `palette.html` | **Vibe Palette** — type a feeling ("cozy rainy Portland coffee shop at dusk") and get a 5-color palette with poetic names and copy-paste CSS variables. Click any swatch to copy its hex; regenerate to remix. |
| 03 | `sticky-wall.html` | **Live Sticky Wall** — the whole room joins with a name and posts one-word answers that fly onto a shared wall in real time. Repeated words merge into giant "×N" stickies, so the audience builds a word cloud together. |
| — | `index.html` | Demo hub — a landing page linking to all three. |

## How the demos work under the hood

- **Vibe Palette** runs its "AI" fully offline: a hashed deterministic seed + hand-tuned word→hue lexicon map language to color, so every prompt renders instantly with zero API cost. Swapping in a real LLM call is a one-function change.
- **Sticky Wall** syncs **across different browsers and devices** via MQTT over WebSockets on a public broker (no accounts, no API keys) using the MQTT.js CDN. Everyone who enters the **same room code** shares the same wall, including full state replay for latecomers. Room can be preset with `?room=your-code` in the URL. If the broker or CDN is unreachable, it falls back to **BroadcastChannel** (same-browser tabs) and shows a status pill so you're never left guessing.
- **Flashcard Quiz** keeps a plain in-memory tally: score, misses, and a live progress bar over 8 cards.

## Run it locally

Just open any HTML file in your browser — double-click, or:

```bash
# e.g. with Python (any static server works)
python3 -m http.server 8000
# then visit http://localhost:8000
```

Static file hosting works too — that's exactly how the GitHub Pages deployment runs.

## Built for

The Claude Builder community, as a live AI build-along session. Gnarly details worth noting if you rebuild any of these:

- The quiz color-codes correct/wrong answers and reveals a one-line explanation before advancing.
- The palette engine is deterministic: the same prompt produces the same family of results, with a remix seed for variation.
- The sticky wall deduplicates words (case-insensitive), tallies authors, and handles prompt shuffles and wall-clears across every connected client (any browser or device).

---

## Credits

Built live with AI assistance as a public demonstration of what a single 15-minute session with an AI coding agent can produce. Copy freely, rebuild often, and try making your own version.
