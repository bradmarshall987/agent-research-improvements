# Schema — the rules of this map

The closed set of node types, the labels they carry, and the naming they follow. When practice and this file disagree, reconcile the same day — schema drift is how structures rot.

## Node types

| `type:` | Lives at | Carries |
|---|---|---|
| `object` (noun) | `objects/<slug>.md` | Why this shape / Shape / Connected to / If you change this / Surfaces / See |
| `process` (verb) | `processes/<slug>.md` | Input → Movement → Output / Steps / If you change this / See |

(Subject-level types — team, job, data-asset, governance, pattern — apply to a *Context map* form, not System map. This repo is a System map: nouns + verbs + effects. No team/process layer.)

## Labels that make it queryable

`type` (object/process), `universe` (live/leftover/ghost), `cluster` (data-acquisition / processing / delivery / hitl / durability / infrastructure), `status` (stub / verified / stale).

For capabilities specifically: `cap_id` (e.g. `cap-001`), `effort` (S / M / L), `hermes_native` (true = prompt+skill change; false = needs external infra), `disposition` (OPEN / SHIPPED / DEFERRED / REJECTED — mirrors ROADMAP.md).

## Naming

- **Slugs**: kebab-case. Capability slugs match `cap-NNN` (zero-padded). Other nouns use topic-role.
- **Object cards**: `objects/<noun-slug>.md` (one card per noun). Capability cards live at `objects/cap-NNN-<short-slug>.md`.
- **Process cards**: `processes/<verb-slug>.md`. Real movements only — no invented sixth.
- **Index file**: `objects/_index.md` — one line per noun, with status.

## Conventions

- A card with `status: stub` is intentionally incomplete; later slices (2/3) fill it in. Stubs are allowed.
- A card with `status: verified` must include a date and citations (`path:line` or owning-file path).
- A card with `status: stale` is allowed when the underlying subject has moved but the card hasn't been re-verified.
- A confident wrong date is **not** allowed. If you can't verify, leave `status: stub`.