# Live Nation MSA Foundation — ICTRecht viewer

Single-page HTML viewer of Narrative's MSA Foundation document (Live Nation Group engagement) prepared for review by Bram (ICTRecht).

**Live**: <https://wytze-narrative.github.io/narrative-tools/ictrecht/live-nation-msa/>

## What's inside

- `index.html` — viewer shell (sticky TOC, search, status legend, ICTRecht-focus filter, print stylesheet)
- `msa-foundation.md` — content. Trimmed copy of Narrative's internal working document. Internal-only sections (interview progress tracking, Wytze's to-do, related-document references that ICTRecht can't access) are stripped.

## Updating the content

When the canonical foundation document changes in Narrative's second brain:

```bash
cp "/Users/wytzedehaan/dev/second-brain-wytze/projects/Live Nation Group/agreements/msa-template-foundation.md" \
   "/Users/wytzedehaan/dev/narrative-tools/ictrecht/live-nation-msa/msa-foundation.md"
```

Then re-apply the trim (top intro block, Voortgangsstatus interview section, Open vragen / to-do voor Wytze section, final iteratief-gevuld footer) — see git history of this file for the exact pattern. Commit + push, GitHub Pages picks it up in ~30s.

## Why a separate trimmed copy

The narrative-tools repo is the external-deelversie. The canonical version in second-brain stays untouched for our own tracking (voortgang, to-do, internal references).
