# Rentman → Ronnie Materiaallijst Converter

Converts a Rentman Excel export (`.xlsx`) into the markdown format the Rentman Ronnie Custom GPT uses as its knowledge base.

**Live tool:** <https://wytze-narrative.github.io/narrative-tools/rentman-converter/>

## How it works

1. User exports materials from Rentman as `.xlsx` with six specific columns (instructions on the page).
2. User drops the file into the tool.
3. SheetJS parses the workbook client-side — the file never leaves the browser.
4. Tool validates the six required columns, maps them to the GPT's markdown format, escapes pipes and multilines.
5. User copies the output or downloads a `.md` file and uploads it to the Custom GPT's knowledge base.

No server, no storage, no tracking. Everything happens in the browser.

## Required Rentman export columns

The tool accepts these headers (case-insensitive, whitespace-trimmed):

| Field | Accepted header names |
|-------|----------------------|
| ID | `ID` |
| Code | `Code` |
| Name | `Naam (in database)` |
| Stock | `Huidig aantal` |
| Type | `Verhuur/verkoop` |
| Location | `Locatie in magazijn`, `Locatie`, `Magazijn locatie`, `Location in warehouse` |

If any column is missing, the tool shows a specific error naming the missing column.

## Companion CLI

A Python version of the same logic lives in the Narrative second brain at `tools/rentman-materiaallijst-converter/convert.py` for headless workflows.
