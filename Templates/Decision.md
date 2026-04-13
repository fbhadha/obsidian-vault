---
type: decision
date: <% tp.date.now("YYYY-MM-DD") %>
project: <% await (async () => { const files = app.vault.getMarkdownFiles().filter(f => f.path.startsWith('Projects/')); const names = files.map(f => f.basename); const pick = await tp.system.suggester(names, names); return pick ? '[[' + pick + ']]' : ''; })() %>
status: <% tp.system.suggester(["Proposed", "Decided", "Revisited", "Reversed"], ["proposed", "decided", "revisited", "reversed"]) %>
decided-by: []
---

## Decision


## Context


## Options Considered


## Rationale

