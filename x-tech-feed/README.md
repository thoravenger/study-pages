# X Tech Feed — Deep Study Notes

Existing Page, updated in place: https://cursor.com/canvas/store-a47a1608-b461-41d4-b4b4-f2ca252b71aa/99ee79cd-a2b7-4f6b-a4a0-db8e73c690f5

Static web copy (GitHub Pages, rebuilt every run): https://thoravenger.github.io/study-pages/x-tech-feed/

12-hourly study notes in Hinglish for Vivek's Java-backend → AI Forward Deployed Engineer preparation. Read-only on X.

## Append-only layout

- Title, six topic tabs (`ai`, `java`, `sys`, `devops`, `courses`, `saved`), By-time filter, search, and all 65 historical collapsible card bodies are preserved.
- One self-contained canvas module; no relative imports or external data-file imports are supported.
- `CARDS` metadata + structured bodies for new cards; immutable historical JSX bodies in `LEGACY_BODIES`, joined by ID and rendered generically.
- New objects append at `// @@APPEND_CARDS_HERE@@`; run labels append at `// @@APPEND_RUNS_HERE@@`. Latest-run and seen-count values use dedicated start/end markers.
- Topic index and time options update automatically. New card headers show usefulness rating, reason, action, and IST run label.
- Full seen IDs/cursor are outside the Page in `latest.json`; the Page keeps only a count and its historical run audit.

## Files

| File | Purpose |
|---|---|
| `ROUTINE_FORMAT.md` | Exact small-file-only procedure, anchors and card template |
| `latest.json` | Authoritative cursor, lastRunIST and seenIds (593 at migration) |
| `page.canvas.tsx` | Local mirror of the published Page source; runs update it with `sync_local.py`, never read it whole |
| `sync_local.py` | Applies a run's EditCanvas edits (JSON list of old/new strings) to `page.canvas.tsx` |
| `build_static.py` + `builder/` | Renders `page.canvas.tsx` to a standalone `index.html` (esbuild + React SSR with HTML stand-ins for `grok/canvas`); checks every card title is present |
| `publish.sh` | Builds and pushes to `thoravenger/study-pages` → `x-tech-feed/`; commits only on change, never force-pushes |
| `index.html` | Existing lightweight pointer |

Latest source run retained: **11 Nov 2026, 1:15 PM IST (Asia/Calcutta)**. Migration adds no study content and does not touch X. Successful EditCanvas compilation/publish verified; byte-for-byte comparison confirmed all 65 historical card bodies unchanged. Since 13 Nov 2026 each run also publishes the static copy with `publish.sh`.
