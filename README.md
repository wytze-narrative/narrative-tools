# Narrative Tools

Small, self-service tools for Narrative clients. Each tool is a single static HTML page — no install, no account, nothing to run locally.

Hosted via GitHub Pages at <https://wytze-narrative.github.io/narrative-tools/>.

## Tools

| Tool | Who | What it does |
|------|-----|--------------|
| [rentman-converter](./rentman-converter/) | Brownys Event Productions | Converts a Rentman Excel export into the markdown format the Rentman Ronnie Custom GPT uses as its knowledge base. |

## Adding a new tool

1. Create a folder at the repo root (e.g. `my-tool/`).
2. Drop in a self-contained `index.html` with inline CSS/JS. Use CDNs for libraries.
3. Add the tool to the table above.
4. Commit. GitHub Pages picks it up automatically.

## Why static

Every tool here is a pure function: input in → output out, no state. There is no reason to run a backend. Static HTML means zero deploys to maintain, zero auth to configure, and the tools keep working as long as GitHub Pages does.
