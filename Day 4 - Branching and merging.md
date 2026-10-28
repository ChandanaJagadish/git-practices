# Day 4: Git and GitHub, Branching and Merging

## Key ideas
- **Branch:** an independent line of development. You can work on a feature or bug fix without touching the main line.
- **Branching:** like a tree with a trunk (`main`) and branches growing from it. Different tasks proceed in parallel, the way family members split up the work of making breakfast.
- **Merging:** combining changes from one branch into another.

**Workflow:** create a branch → work independently → review → merge into `main`.

## Why use branches?
| Use | Example |
|---|---|
| Individual: try different approaches | Build a simple login page on one branch and a vintage-style one on another, then merge the one you prefer. |
| Team: work without interfering | One developer builds the login page, another the homepage, another fixes a bug. Each works on a separate branch. |

## Practice: portfolio website
Files: `index.html`, `style.css`, `script.js`

**1. Set up the repo**
```bash
cd portfolio
git init
git add .
git commit -m "Create initial portfolio website"
git status          # should say the working tree is clean
```

**2. Usual commit cycle:** modify → `git status` → `git add <file>` → `git status` → `git commit -m "message"`
```bash
git log --oneline   # view compact history
```

**3. Create and use a branch**
```bash
git branch fix-one      # create (stay on current branch)
git switch fix-one      # move to it
git branch              # list branches; * marks the current one
```
A new branch starts from the same commit as `main`. Changes committed on `fix-one` do not appear on `main`.

**4. Change something on `fix-one`, then commit**
```bash
git add index.html
git commit -m "Update portfolio on fix-one branch"
git switch main         # the fix-one change is not here yet
```

**5. Merging**
```bash
git switch main
git merge fix-one
```
`git merge fix-one` merges `fix-one` into the branch you are on, so always check your current branch first.

## Branching commands
| Command | Purpose |
|---|---|
| `git branch name` | Create a branch |
| `git switch name` or `git checkout name` | Switch to a branch |
| `git switch -c name` or `git checkout -b name` | Create a branch and switch to it |
| `git branch` | List local branches |
| `git merge name` | Merge `name` into the current branch |

## Merge conflicts
A **merge conflict** happens when Git cannot combine changes automatically, for example when two branches edit the same line differently.

**Try it:**
```bash
git switch -c fix-add
# edit line 4 of style.css (e.g. color: red;)
git add style.css
git commit -m "Update line 4 in fix-add"

git switch main
# edit the same line 4 differently (e.g. color: blue;)
git add style.css
git commit -m "Update line 4 in main"

git merge fix-add       # Git reports a conflict
```
Git pauses the merge because it cannot tell which colour to keep. Editing the same line does not always cause a conflict, but here Git cannot reconcile the two changes, so you must resolve it by hand.

## Summary
- Branches let you develop changes independently.
- `switch` moves between branches; `switch -c` creates and switches in one step.
- `merge` brings one branch's changes into the current branch.
- A merge conflict means Git needs you to choose between competing changes.

**Next:** find the conflicting lines, choose the right changes, and finish the merge.
