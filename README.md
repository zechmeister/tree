# tree

Create git worktrees for branches and switch to them. Useful for working with multiple LLM agents in parallel on different branches.

## What it does

Creates a git worktree for the specified branch in `../<repo>-worktrees/<branch-name>`, copies any paths listed in `.worktreeinclude` (one per line, `#` for comments), and opens a shell in the new worktree.

If the argument is a number, it's treated as a PR: the worktree is created at `../<repo>-worktrees/pr-<number>` with the PR's real branch inside.

## Setup

1. Symlink into your bin directory:

   ```bash
   ln -s "$PWD/tree" ~/bin/tree
   ```

2. Make sure `~/bin` is in your PATH (add to `.zshrc` if needed):
   ```bash
   export PATH="$HOME/bin:$PATH"
   ```

## Usage

```bash
tree <branch-name>   # worktree a branch (created from HEAD if missing)
tree <pr-number>     # fetch a PR from origin and worktree it as pr-<number>
```
