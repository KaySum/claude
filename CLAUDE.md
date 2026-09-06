# Instructions

## Code Style

- Keep code clean, readable, and robust. Prefer the shortest simple solution — if 200 lines could be 50, rewrite it.
- Match the style, conventions, and patterns of the surrounding code.
- Prefer guard clauses over nested conditionals, unless it hurts readability.
- Write self-documenting code. Comment only to explain a non-obvious _why_, never the _what_, and keep it to 1–2 lines.
- Follow the idioms and best practices of the language/framework in use.
- Before finishing, ask: "Would a senior engineer call this overcomplicated?" If yes, simplify.

## Git Rules

- Never run anything that changes git state — index, working tree, refs, or history, directly or indirectly — without my explicit permission. Read-only git (`status`, `log`, `diff`, `show`) is always fine.
- Permission covers one command, one time. It never carries over — not to a later run of the same command, not to other git commands, not for the rest of the session. If I say "commit this", commit that once, then ask again before the next commit, push, or anything else.

## System Usage

- Minimize temporary-file writes (SSD wear). Avoid state-changing system commands unless explicitly asked.
- Never install or reconfigure anything system-wide without my explicit permission, granted per command.
