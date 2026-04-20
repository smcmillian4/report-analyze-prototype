# Reports "About / Analyze" Tab — Interactive Prototype

Interactive prototype for the two-tier About/Analyze tab in Reports. Single HTML file, zero dependencies.

## Live demo

Open `index.html` in any browser, or visit the GitHub Pages URL after enabling Pages on this repo.

## Toggle controls

Use the pill buttons at the top to switch between states:

| Toggle | What it does |
|--------|-------------|
| **AI SKU** | Switches between base tier ("About") and AI tier ("Analyze"). AI tier shows data-aware analysis insights with per-finding chat affordances. |
| **Upsell** | Shows a blurred preview + upgrade CTA when AI SKU is off. This is the marketing gate for non-AI customers. |
| **Outdated** | Shows a warning banner indicating analysis is stale (data changed since last generation). Only visible in AI tier. |
| **Markdown** | Toggles between the rich card-based view and a prose/markdown-style rendering of the same content. |

## Architecture (maps to real implementation)

- **Base tier** — deterministic config description (no AI, no backend calls). Always available.
- **AI tier** — config description + AI-generated data analysis. Gated by `analytics-report-ai-analysis` feature flag.
- **Upsell** — static teaser card, gated by a separate `analytics-report-ai-upsell` feature flag. No backend calls needed.
- **Per-finding affordance** — each insight card has a persistent star icon that triggers a "Tell me more about: {finding}" handoff to Rippling AI copilot chat.

## Editing

Everything is in a single `index.html`. Edit directly — no build step required.
