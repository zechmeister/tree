# tree

Create git worktrees for branches and switch to them. Useful for working with multiple LLM agents in parallel on different branches.

## What it does

Creates a git worktree for the specified branch in `../<repo>-worktrees/<branch-name>`, copies any paths listed in `.worktreeinclude` (one per line, `#` for comments), and opens a shell in the new worktree.

If the argument is a number, it's treated as a PR: the worktree is created at `../<repo>-worktrees/pr-<number>` and `gh pr checkout` sets up the PR's real branch inside it with the correct remote and push config. So the directory stays namespaced as `pr-<number>` (easy to find later), while the branch is the contributor's actual branch — meaning `git push` from the worktree updates the PR (including PRs from forks that allow maintainer edits). The PR is looked up on the `origin` remote (so multi-remote repos don't need `gh repo set-default`). Requires the [`gh` CLI](https://cli.github.com/), authenticated.

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
