---
name: git-rescue
description: Recover "lost" commits and undo git oops moments using reflog and reset. Use when the user lost commits, did a bad reset, wants to undo a merge/rebase, or says they "accidentally" did something in git.
---

# Git Rescue

*Your commits are not lost. Stay calm. We'll find them.*

Helps recover "lost" commits and undo common git oops moments. Uses `git reflog` and careful reset/revert so nothing is truly gone until the reflog expires.

## When to Apply

- User says they lost commits, did a bad reset, or want to undo a merge/rebase
- User says they "accidentally" did something in git
- User wants to get back to a previous state or find a "deleted" commit
- User mentions reflog, recovering commits, or undoing a reset

## The Golden Rule

**Reflog is your safety net.** Git keeps a log of where HEAD (and other refs) have been. Commits are only garbage-collected after they're unreachable for a while. So: don’t panic, don’t run `git gc --prune=now`.

## Workflow

1. **Assess the situation**
   - Run `git reflog` (and optionally `git reflog show --all` if they mention a specific branch).
   - Run `git status` and `git log -1` so you know current branch and latest commit.

2. **Find the "lost" commit**
   - In reflog, look for the commit hash or message they want to get back to (e.g. "commit: my important work", "reset: moving to ...", "merge", "rebase").
   - Note the full hash of that commit (e.g. `abc1234`).

3. **Recover or rewind**
   - **Just want to look?**  
     `git show <hash>` — no changes, just inspect.
   - **Want the branch to point there again (discard everything after)?**  
     `git reset --hard <hash>` — branch now points at that commit; working tree matches.  
     Use only when they’re sure they want to drop newer commits on this branch.
   - **Want to bring that commit back as a new commit on top of current state?**  
     `git cherry-pick <hash>` — reapplies that commit. Good for "I want that one commit back."
   - **Undo a merge (no push yet)?**  
     `git reset --hard ORIG_HEAD` or `git reset --hard <commit-before-merge>` from reflog.
   - **Undo a rebase?**  
     Find the pre-rebase tip in reflog (e.g. "rebase (start)") and `git reset --hard <that-hash>`.

4. **Confirm**
   - Run `git log -3` (or show the relevant reflog line) and briefly say what you did so the user sees the branch is back where they wanted.

## Rules

- **Do not** run destructive commands (e.g. `git reset --hard`, `git clean -fd`) without the user having asked to recover/undo. Prefer showing reflog and suggesting the exact command first if the situation is ambiguous.
- **Do not** run `git gc --prune=now` or anything that might purge reflog entries.
- Prefer **non-destructive** options when possible: e.g. show the hash and suggest `git cherry-pick` or `git reset --hard` and let the user confirm, unless they clearly said "restore to that commit" or "undo the reset."
- Keep the tone light and reassuring ("We found it", "That commit is still in reflog", "One more step and you’re back") but keep instructions precise.

## One-Liners to Remember

- **"Where did I leave my branch?"** → `git reflog`
- **"I want this branch to be exactly like that commit again."** → `git reset --hard <hash>`
- **"I want that one commit on top of where I am now."** → `git cherry-pick <hash>`
- **"I just merged and I hate it."** → `git reset --hard ORIG_HEAD` (if not pushed)

## Optional: Add a Dad Joke

If the user seems stressed, you may include exactly one rescue-themed pun, for example:

- "Your commits were just taking a nap in the reflog."
- "We don’t lose commits here. We *misplace* them temporarily."
- "Git: the only place where 'undo' is actually possible."

Then get back to the rescue steps.
