# Work Vault Setup Guide

## Folder Structure

Create these folders in your vault root:

```
/People
/Projects
/Meetings
/Decisions
/Notes
/Templates
/Bases
```

## Plugin Setup

### Required

1. **Bases** (Core Plugin): Settings → Core Plugins → Enable "Bases"
2. **Templater** (Community Plugin): Settings → Community Plugins → Browse → Install "Templater"
3. Disable the core **Templates** plugin to avoid conflicts

### Templater Configuration

In Settings → Templater:

1. Set "Template folder location" to `Templates`
2. Enable "Trigger Templater on new file creation"
3. Under "Folder Templates", map each folder to its template:
   - `People` → `Templates/Person.md`
   - `Projects` → `Templates/Project.md`
   - `Meetings` → `Templates/Meeting.md`
   - `Decisions` → `Templates/Decision.md`
   - `Notes` → `Templates/Note.md`

## File Placement

- Copy all `.md` files from this package into `/Templates`
- Copy all `.base` files into `/Bases`

## How the Connections Work

### When you open a Project note, you see:

- **Related Meetings** — all meetings where the `project` property links to this project
- **Open Decisions** — all decisions linked to this project with `status: proposed`
- **Related People** — all people linked from this project's `stakeholders` property

### When you open a Person note, you see:

- **Related Projects** — all projects where this person is in `stakeholders`
- **Related Decisions** — all decisions where this person is in `decided-by`
- **Meeting History** — all meetings where this person is in `attendees`

### Sidebar (always visible):

- **Recent Meetings** — last 20 meetings across all projects, sorted by date
- **All Open Decisions** — every decision with `status: proposed`, across all projects

To add a base to your sidebar: open the `.base` file, then drag its tab into the left or right sidebar panel.

## Property Types

Set these in Settings → Properties (or by clicking a property name in any note):

| Property | Type |
|---|---|
| type | Text |
| role | Text |
| team | Text |
| org | Text |
| relationship | Text |
| last-contact | Date |
| status | Text |
| stakeholders | List |
| started | Date |
| date | Date |
| project | Text |
| attendees | List |
| meeting-type | Text |
| decided-by | List |
| tags | List |

## Property Values Reference

These are the values the Templater suggesters will offer. Obsidian will autocomplete them after first use.

- **status** (Projects): active, paused, completed, proposed
- **status** (Decisions): proposed, decided, revisited, reversed
- **relationship** (People): stakeholder, peer, report, vendor, skip-level
- **meeting-type** (Meetings): standup, 1:1, review, planning, ad-hoc
- **org** (People): Acme, Vendor, Other

## Workflow Tips

- When creating a meeting, add attendees as `[[links]]` to People notes. This is what makes Meeting History work on Person notes.
- When creating a project, add stakeholders as `[[links]]`. This is what makes Related Projects work on Person notes.
- When creating a decision, add decided-by as `[[links]]`. This is what makes Related Decisions work on Person notes.
- The `project` property on Meetings and Decisions should be a single `[[link]]` to a Project note.
- If a base shows no results, check that your property values match exactly — `[[Project Name]]` in the property must match the actual filename of the project note.
