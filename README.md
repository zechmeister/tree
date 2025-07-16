# tree

Create git worktrees for branches and switch to them. Useful for working with multiple LLM agents in parallel on different branches.

## What it does

Creates a git worktree for the specified branch in `../<repo>-worktrees/<branch-name>`, copies `.env.local` if exists, and opens a shell in the new worktree.

## Setup

1. Copy to your bin directory:

   ```bash
   cp tree ~/bin/tree
   chmod +x ~/bin/tree
   ```

2. Make sure `~/bin` is in your PATH (add to `.zshrc` if needed):
   ```bash
   export PATH="$HOME/bin:$PATH"
   ```

## Usage

```bash
tree <branch-name>
```
