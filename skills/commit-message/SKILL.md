---
name: commit-message
description: Write a one-line commit message for the staged changes. Use when the user asks for a commit message, says "/commit-message", "write the commit", "what should I call this commit", or is about to commit and wants wording. Produces the message only — it never runs git commit.
---

# Commit Message

Produce **one line** that a reviewer could read six months later and know *why* the change exists and *how* it was done.

## 1. Gather context

Run these together:

```bash
git diff --staged --stat
git diff --staged
git log --oneline -15
```

- Nothing staged? Say so, show `git status --short`, and stop. Do not stage anything.
- Huge diff? Read `--stat` first, then the diff of the files that carry the intent (skip lockfiles, generated output, formatting-only churn).
- `git log` is the source of truth for this repo's conventions — match its prefix style, casing, and tense rather than any default.

## 2. Use the conversation

If the work was done earlier in this session, the diff shows *what* changed but the conversation holds *why*. Prefer the user's stated goal ("the LSP wasn't attaching for C files") over a restatement of the patch ("add clang config"). Ignore the conversation when the staged changes came from somewhere else.

## 3. Write the line

- One line. No body, no bullet list, no trailing period. Aim ≤ 72 chars; hard stop at 90.
- Conventional prefix taken from the log (`feat:`, `fix:`, `chore:`, `docs:`, `refactor:`), imperative mood.
- Scope in parens — `feat(auth):` — when the log already uses scopes, or when the diff sits in one clear area (a package, module, or surface) and naming it saves words in the summary. Use the name the repo uses, lowercase. Skip it when the change spans several areas or when the scope would just repeat the summary; a bare `feat:` is fine.
- Lead with the intent — the outcome or problem solved. Append the mechanism only when it isn't obvious from the outcome, joined naturally (`by`, `via`, `using`, `with`).
- One commit, one idea. If the staged changes are two unrelated ideas, say so and offer a split instead of writing an `and` message.
- Never add attribution, co-author trailers, or tool footers.

Good:

```
fix(webhooks): stop duplicate deliveries by keying retries on event id
feat(lsp): add clang server for C and C++ buffers
refactor(parser): collapse the three passes into one walk
perf(search): cut cold query time by indexing tags at write
docs: explain why the retry queue is capped at 500
feat: add clang LSP
```

Weak — restates the diff, hides the intent, or scopes badly:

```
fix: update handler.ts and config.json     # what for?
feat: add retryKey field                   # implementation, not intent
chore: various improvements                # says nothing
fix(fix): correct the fix                  # scope carries no information
feat(src): add rate limiting               # "src" is not an area
refactor(auth): refactor auth              # scope just repeats the summary
```

## 4. Output

Print the message alone in a fenced block so it can be copied. Add at most one short sentence if a caveat matters (unrelated changes staged, generated files included).

**Do not run `git add`, `git commit`, or `git push`** — even if the message looks final. The user commits.
