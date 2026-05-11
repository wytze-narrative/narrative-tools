# Live Nation MSA Foundation — ICTRecht viewer

Single-page HTML viewer of Narrative's MSA Foundation document (Live Nation Group engagement) prepared for review by Bram (ICTRecht).

**Live**: <https://wytze-narrative.github.io/narrative-tools/ictrecht/live-nation-msa/>

## What's inside

- `index.html` — viewer shell (sticky TOC met genummerde badges, search, status legend, ICTRecht-focus filter, print stylesheet, accessibility hooks)
- `msa-foundation.md` — content. Trimmed copy of Narrative's internal working document. Internal-only sections (interview progress tracking, Wytze's to-do, working-document reasoning paragraphs, related-document references that ICTRecht can't access) are stripped.

## Updating the content

When the canonical foundation document changes in Narrative's second brain, copy the file and **re-apply the trim** afterwards:

```bash
cp "/Users/wytzedehaan/dev/second-brain-wytze/projects/Live Nation Group/agreements/msa-template-foundation.md" \
   "/Users/wytzedehaan/dev/narrative-tools/ictrecht/live-nation-msa/msa-foundation.md"
```

The trim consists of five edits — see git history of `msa-foundation.md` for the exact diffs, but in summary:

1. **Strip `✅` markers** from all `### Sectie X — …` H3 headings (working-document residue).
2. **Simplify the groepstructuur block** under `### De groepsstructuur (vanaf 1 juli 2026)` — drop personal-holding tree (Runtime / Springway / D'urso), use the one-pager phrasing: "Part of the Narrative B.V. — Wytze + Xander 50/50; Part of the Protocol B.V. — Wytze + Xander + Bjorn ieder 1/3."
3. **Strip personal-holding references** at the Sectie 1 aandeelhouders bullet and the illustratieve MSA-clausule ("within Service Provider's corporate group" instead of "within the Runtime Holding group").
4. **Delete four internal-reasoning H3 sections** under Achtergrond: "Wat als een opdracht gemengd is?", "Bjorn Veldmeijer — implicaties voor MSA", "Mogelijk later: AV v1.3 audit", "Toekomstige enterprise-klanten — pattern".
5. **Rewrite the Decisions Log intro line** (just below `## Decisions log`) from "Elke sectie hieronder wordt pas ingevuld zodra we er in het interview doorheen zijn." to the Bram-facing handoff phrasing about voorgenomen posities + ⚠️ markers + filter button.

Then in the doc top-block, replace the H1 + Start/Status/Eigenaar/Relateerde-documenten fields, change `## 0. Interview-roadmap` to `## Overzicht — onderwerpen per fase`, drop the Status column from all six Fase tables (Sectie 13 entry mentions "(gemerged in Sectie 6c)" inline). Truncate at the bottom — remove `## Voortgangsstatus interview`, `## Open vragen / to-do voor Wytze`, and the final iteratief-gevuld footer.

End the file with an HTML comment noting: `<!-- internal sections (Voortgangsstatus interview, Open vragen / to-do voor Wytze) removed for ICTRecht-facing version — see canonical document in second-brain -->`

Commit + push, GitHub Pages picks it up in ~30s.

## Why a separate trimmed copy

The narrative-tools repo is the external-deelversie. The canonical version in second-brain stays untouched for our own tracking (voortgang, to-do, internal references).
