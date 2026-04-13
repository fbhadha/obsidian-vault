---
type: person
role: <% tp.system.prompt("Role title") %>
team: <% tp.system.prompt("Team") %>
org: <% tp.system.suggester(["Acme", "Vendor", "Other"], ["Acme", "Other", "Other"]) %>
relationship: <% tp.system.suggester(["Stakeholder", "Peer", "Direct Report", "Vendor", "Skip-Level"], ["stakeholder", "peer", "report", "vendor", "skip-level"]) %>
last-contact: <% tp.date.now("YYYY-MM-DD") %>
---

## Notes


## Related Projects

![[Related Projects.base]]

## Related Decisions

![[Related Decisions for Person.base]]

## Meeting History

![[Meeting History.base]]
