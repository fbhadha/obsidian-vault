---
type: meeting
date: <% tp.date.now("YYYY-MM-DD") %>
project: <% await (async () => { const files = app.vault.getMarkdownFiles().filter(f => f.path.startsWith('Projects/')); const names = files.map(f => f.basename); const pick = await tp.system.suggester(names, names); return pick ? '[[' + pick + ']]' : ''; })() %>
attendees: []
meeting-type: <% tp.system.suggester(["Standup", "1:1", "Review", "Planning", "Ad-hoc"], ["standup", "1:1", "review", "planning", "ad-hoc"]) %>
---

## Context


## Notes


## Action Items

- [ ] 

## Decisions Made

