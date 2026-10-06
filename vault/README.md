# Algorithms vault

Obsidian vault for algorithm theory and solved problems. In Obsidian: **Open folder as vault**, choose this `vault/` folder, then open `00 - Index`.

## Layout
- `Patterns/`, `Data Structures/`, `Problems/`: one note each, with a map-of-content note per folder
- `Cheatsheets/`: Big-O and Python reminders
- `Templates/`: Pattern, Data Structure, Problem (Settings > Templates is already pointed here)

## Conventions
- Every note starts with YAML properties (`type`, `tags`; problems also `difficulty`, `pattern`, `time`, `space`, `status`).
- Link with `[[wikilinks]]`: problem -> pattern -> data structure, so the graph view shows clusters.
- Code lives in fenced `python` blocks inside the notes.
- No plugins required. New notes are created in `Problems/` by default.

## Add a problem
1. New note in `Problems/`, then insert the Problem template.
2. Fill in the sections, link the pattern note.
3. Add a row to `Problems/Problems.md` and a link in the pattern note.
