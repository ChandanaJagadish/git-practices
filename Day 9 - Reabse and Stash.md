# Day 9 – Git Rebase and Stash

Today, we are going to learn two important Git concepts:

1. Git Rebase
2. Git Stash

## 1. What is Git Rebase?

Rebase means replaying commits from one branch on top of another branch's latest commit.

Let's understand this with a team collaboration example.

### Real-world scenario

Imagine you and your teammate are working on the same project.

- Your teammate creates a branch and starts working on adding a footer.
- You create another branch and start working on adding a login page.

Both of you created your branches from the same `main` branch.

Now, your teammate finishes the footer and merges their changes into `main`.

The `main` branch is now updated, but your branch still has the older version of `main` from when you created it.

Problem: How will you get the latest changes from `main` into your branch without losing your login-page work?

This is where Git Rebase comes into the picture.

You can rebase your branch onto the updated `main` branch.

Git takes the commits you made on your branch and replays them on top of the latest commit in `main`.

### Visual representation of Rebase

Before rebase:

```
          C1---C2  (main)
         /
A---B
     \
      L1---L2  (feature-login)
```

Here:

- `A` and `B` are common commits.
- `C1` and `C2` are your teammate's commits.
- `L1` and `L2` are your login-page commits.

After rebase:

```
A---B---C1---C2---L1'---L2'  (feature-login)
             (latest main)
```

Your login-page commits are replayed on top of the latest `main` commit.

Notice that `L1'` and `L2'` represent new commits created by the rebase. They contain the changes from your original commits, but have new commit IDs.

### Commands to perform Rebase

First, switch to the branch that contains the latest changes:

```
git switch main
```

Then switch to your feature branch:

```
git switch feature-login
```

Now rebase your branch onto `main`:

```
git rebase main
```

That's it! Your branch now contains the latest changes from `main`, with your commits replayed on top.

Important: You do not need to merge `main` into your branch after a successful rebase. Rebase has already placed your commits on top of the latest `main` history.

## 2. Difference Between Merge and Rebase

Both merge and rebase help integrate changes from different branches, but they work differently.

### Merge

Merge combines the work from two branches.

It preserves the original branch history and may create a separate merge commit.

```
          C1---C2
         /       \
A---B-------------M  (main)
     \           /
      L1---L2----
```

Here:

- Your teammate's work is represented by `C1` and `C2`.
- Your work is represented by `L1` and `L2`.
- `M` is the merge commit.

### Rebase

Rebase replays your commits on top of another branch's latest commit.

```
A---B---C1---C2---L1'---L2'
```

Here, your work appears after your teammate's work in a linear history.

| Merge                                 | Rebase                                            |
| ------------------------------------- | ------------------------------------------------- |
| Combines branch histories             | Replays commits on top of another branch          |
| May create a merge commit             | Creates new commits with new IDs                  |
| Preserves the original commit history | Rewrites the branch's commit history              |
| Can produce a non-linear history      | Produces a linear history for the rebased commits |

In simple words:

- Merge: Combines your work and your teammate's work while preserving the branch history.
- Rebase: Places your work on top of your teammate's latest work by replaying your commits.

## 3. Practical Example – Rebase Using the Command Line

Let's perform a small practical exercise.

### Step 1: Create a folder and initialize Git

```
mkdir rebase-practice
cd rebase-practice
git init
```

### Step 2: Create a file and commit it

```
touch file1.txt
git add file1.txt
git commit -m "Initial commit"
```

### Step 3: Create your teammate's branch

```
git switch -c teammate
```

Create a file and commit it:

```
touch footer.txt
git add footer.txt
git commit -m "Add footer"
```

### Step 4: Merge the teammate's work into main

```
git switch main
git merge teammate
```

Now `main` contains the footer changes.

### Step 5: Create your own feature branch

```
git switch -c feature-login
```

Create a file and commit it:

```
touch login.txt
git add login.txt
git commit -m "Add login page"
```

Now the `feature-login` branch is behind `main` because it does not contain the teammate's latest commit.

### Step 6: Rebase your branch

Make sure you are on `feature-login` and execute:

```
git rebase main
```

Git will replay your login-page commit on top of the latest `main` commit.

You have now updated your branch using rebase!

## 4. Rebase Conflict

A rebase conflict is similar to a merge conflict.

Suppose:

- Your teammate modifies line 4 of a file in `main`.
- You also modify the same line in your feature branch.
- Git cannot automatically determine which change should be retained.

A conflict occurs.

You need to:

1. Open the file containing the conflict.
2. Decide which changes should be retained.
3. Edit the file to resolve the conflict.
4. Stage the resolved file.
5. Continue the rebase.

Commands:

```
git add filename
git rebase --continue
```

If you want to cancel the rebase and return to the state before it started:

```
git rebase --abort
```

## 5. What is Git Stash?

Git Stash is used to temporarily save your uncommitted changes so that you can work on something else without losing your current work.

### Real-world scenario

Imagine you are working on a login page from scratch.

Suddenly, your teammate approaches you and says:

"We have an urgent issue in the project. Can you fix it immediately?"

But you haven't completed your login-page work yet.

You don't want to commit incomplete code, and you also don't want to lose your progress.

What can you do?

This is where Git Stash comes in.

Git Stash temporarily stores your uncommitted changes so that you can work on something else.

### Commands used in Git Stash

1\. Stash your current changes

```
git stash
```

This saves your tracked, uncommitted changes and gives you a clean working directory.

2\. View your stash list

```
git stash list
```

This displays all the stashed changes.

Example:

```
stash@{0}: WIP on main: ...
stash@{1}: WIP on feature-login: ...
```

3\. Apply the latest stash

```
git stash apply
```

This restores the latest stashed changes but keeps them in the stash list.

4\. Apply and remove the latest stash

```
git stash pop
```

This restores the latest stashed changes and removes that stash entry if the application succeeds.

5\. Remove a stash entry

```
git stash drop
```

This removes the latest stash entry without applying it.

6\. Clear all stash entries

```
git stash clear
```

This removes all stored stash entries.

### Example workflow

1. You are working on your login page.
2. An urgent issue arrives.
3. You temporarily save your work using `git stash`.
4. You switch to the appropriate branch and fix the urgent issue.
5. You commit the urgent fix.
6. You return to your login-page branch.
7. You restore your earlier work using `git stash pop`.
8. You continue developing the login page.

Your unfinished work is now restored!

Important: By default, `git stash` saves changes to tracked files. New untracked files are not included unless you use:

```
git stash -u
```

## 6. Quick Revision

| Command                 | Purpose                                                            |
| ----------------------- | ------------------------------------------------------------------ |
| `git rebase main`       | Replays the current branch's commits on top of main                |
| `git rebase --continue` | Continues a rebase after resolving conflicts                       |
| `git rebase --abort`    | Cancels the ongoing rebase                                         |
| `git stash`             | Temporarily saves uncommitted tracked changes                      |
| `git stash list`        | Displays saved stashes                                             |
| `git stash apply`       | Restores a stash without removing it                               |
| `git stash pop`         | Restores and removes the latest stash after successful application |
| `git stash drop`        | Removes a stash entry                                              |
| `git stash clear`       | Removes all stash entries                                          |

That's it for Day 9 – Git Rebase and Stash!