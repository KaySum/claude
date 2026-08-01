# Claude Code Configuration

Personal configuration for
[Claude Code](https://claude.com/claude-code), living in `~/.claude`.

## Install

These files belong in your `~/.claude` directory. Pick one of the approaches
below.

### Symlink (recommended)

Clone anywhere and symlink the files, so `git pull` keeps your config up to date:

```sh
git clone https://github.com/KaySum/claude-config.git ~/claude-config
ln -sf ~/claude-config/CLAUDE.md ~/.claude/CLAUDE.md
ln -sf ~/claude-config/settings.json ~/.claude/settings.json
```

### Copy

Or just copy the files in:

```sh
git clone https://github.com/KaySum/claude-config.git
cp claude-config/CLAUDE.md claude-config/settings.json ~/.claude/
```

> **Note:** `~/.claude` also holds machine-local state (sessions, caches,
> history). Back up any existing `CLAUDE.md` and `settings.json` before
> overwriting them.

## Update

```sh
cd ~/claude-config && git pull
```

If you copied the files instead of symlinking, re-run the copy step after pulling.
