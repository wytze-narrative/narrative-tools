# Narrative Tools

Custom self-service tools we ship for Narrative clients. Each tool is a single static HTML page — no install, no account, no backend.

Hosted via GitHub Pages at <https://wytze-narrative.github.io/narrative-tools/>.

## Structure

Tools live under per-client folders so each client only knows about their own work:

```
brownys/
  rentman-converter/     — Brownys Event Productions
qdance/
  ...                    — (future)
```

The root landing page intentionally lists no tools. Clients receive a direct deep link to their own tool.

## Adding a new tool

1. Create the client folder if it doesn't exist (e.g. `mkdir clientname`).
2. Add a tool subfolder with a self-contained `index.html` (inline CSS/JS, libraries from CDN).
3. Commit. GitHub Pages picks it up automatically. Send the client the deep link.

## Why static

Every tool here is a pure function: input in → output out. No data leaves the user's browser. No backend means zero deploys to maintain, zero auth to wire up, and the tools keep working as long as GitHub Pages does.

## Why per-client folders

Privacy without login friction. Clients can't browse to or discover other clients' tools, but Eva at Brownys never has to type a password to use a converter she runs once a month.
