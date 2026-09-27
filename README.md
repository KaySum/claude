# claude

Personal configuration for [Claude Code](https://claude.com/claude-code), living
in `~/.claude`.

## Install

1. Point `~/.claude` at the repo. It can't be cloned over, since the directory
   also holds machine-local state (sessions, caches, history):

   ```sh
   cd ~/.claude && git init -q && git remote add origin https://github.com/KaySum/claude.git && git fetch -q origin
   ```

2. Back up whatever the repo is about to overwrite. The list comes from the repo
   itself, so it stays right as the config grows:

   ```sh
   git ls-tree -r --name-only origin/main | while IFS= read -r f; do [ -e "$f" ] && printf '%s\n' "$f"; done | tar -czf ~/claude-backup.tgz -T -
   ```

3. Check out the config on top of yours:

   ```sh
   git checkout -f main
   ```

4. Remove the `.git` folder, so you can add it to your own repo later

   ```sh
   rm -rf ~/.claude/.git
   ```

5. Start Claude Code!

   ```sh
   claude
   ```
