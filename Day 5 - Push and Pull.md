# Day 5: Git and GitHub — First Push and Pull

## 1. What Is Git?

**Git** is a version control tool that runs on your computer. It helps you track changes in your project and manage different versions of your code.

Git can work offline using commands such as:

- `git init` — Initialize a repository.
- `git add` — Stage changes.
- `git commit` — Save a snapshot of changes.
- `git branch` — Manage branches.
- `git merge` — Integrate changes from branches.

## 2. What Is GitHub?

**GitHub** is an online platform that hosts Git repositories. It provides features such as:

- Storing and sharing source code online.
- Pull Requests (PRs).
- Issues and bug tracking.
- Code reviews and collaboration.

**Remember:**
- Git is the version control tool.
- GitHub is an online platform that hosts Git repositories.

## 3. What Is a Local Repository and a Remote Repository?

### Local Repository

A local repository is the Git repository on your laptop, where you work on your project files and commit changes.

### Remote Repository

A remote repository is a version of your repository hosted on a remote server, such as GitHub.

The remote is usually configured using a repository URL. A name such as `origin` is commonly used as the shortcut for that remote.

## 4. What Are Push and Pull?

### Push

**Push** sends your local commits to a remote repository.

Example: You create a project on your laptop, commit your changes, and push them to GitHub so they are available online.

### Pull

**Pull** fetches changes from a remote repository and integrates them into your current local branch.

Example: You edit a file directly on GitHub. Later, you want those changes on your laptop, so you pull them into your local repository.

### Quick Comparison

| Operation | Direction | Purpose |
|---|---|---|
| `git push` | Local → Remote | Send local commits to GitHub |
| `git pull` | Remote → Local | Fetch and integrate remote changes |

## 5. Practical Example: Your First Push

Before starting, create a project folder, add some files, initialize Git, and commit your changes.

### Step 1: Create a Repository on GitHub

1. Log in to your GitHub account.
2. Create a new repository.
3. Give it a suitable name, such as `my-first-project`.
4. For this beginner workflow, create it as an **empty repository** without an initial README, license, or `.gitignore` file.
5. Open the repository page and find the instructions for pushing an existing repository.

### Step 2: Connect Your Local Repository to GitHub

GitHub will provide a command similar to this:

```bash
git remote add origin https://github.com/YOUR-USERNAME/my-first-project.git
```

Replace the example URL with your actual repository URL.

**What does this command mean?**

- `git remote` — Manage connections to remote repositories.
- `add` — Add a new remote connection.
- `origin` — The conventional name for this remote.
- The URL — The location of your GitHub repository.

This command links your local repository to the remote repository. It does not upload your code yet.

You can verify the connection using:

```bash
git remote -v
```

### Step 3: Push Your Local Repository to GitHub

First, check your current branch:

```bash
git branch
```

If your branch is named `main`, push it using:

```bash
git push -u origin main
```

If your branch has a different name, replace `main` with that branch name.

**What does this command mean?**

- `git push` — Upload local commits to a remote repository.
- `-u` — Set the upstream relationship between your local branch and the remote branch.
- `origin` — The remote repository's name.
- `main` — The branch being pushed.

After setting the upstream, future pushes from that branch can usually be done with:

```bash
git push
```

Once the push succeeds, refresh your GitHub repository page to see the uploaded files and commits.

## 6. GitHub Authentication

When pushing through HTTPS, GitHub may ask you to authenticate.

GitHub does not accept your regular account password for Git operations over HTTPS.

Depending on your setup, you can authenticate using:

- Git Credential Manager or another supported sign-in flow.
- A Personal Access Token (PAT), when token authentication is used.
- SSH keys, if your remote URL is configured for SSH.

### Personal Access Token (PAT)

If you use a PAT, create one through GitHub's settings under **Developer settings → Personal access tokens**.

Follow GitHub's instructions and grant only the permissions required for your task. For pushing to a repository, the required permissions depend on the token type and repository access.

**Security reminder:** Treat your token like a password. Never share it, commit it to your code, or paste it into a public repository.

## 7. Practical Example: Pull Changes from GitHub

Suppose you make a change directly on GitHub and now want to bring it to your laptop.

### Step 1: Open Your Local Project

Use the terminal to enter the project folder:

```bash
cd my-first-project
```

### Step 2: Pull the Remote Changes

If your current branch tracks `origin/main`, run:

```bash
git pull
```

Git fetches the remote changes and integrates them into your current branch.

If no upstream is configured, specify the remote and branch:

```bash
git pull origin main
```

If you have uncommitted local changes, Git may ask you to commit or otherwise handle them before integrating the remote changes.

## 8. Important Commands — Quick Revision

| Command | Purpose |
|---|---|
| `git remote -v` | View configured remote URLs |
| `git remote add origin URL` | Connect a local repository to a remote |
| `git push -u origin main` | Push `main` and set its upstream |
| `git push` | Push commits to the configured upstream |
| `git pull` | Fetch and integrate changes from the upstream |
| `git pull origin main` | Pull from `origin/main` explicitly |
| `git status` | Check the state of your files |
| `git log --oneline` | View a compact commit history |

## 9. Key Takeaways

- Git is a version control tool that can work locally and offline.
- GitHub hosts Git repositories online and supports collaboration.
- A local repository is stored on your computer.
- A remote repository is hosted elsewhere, for example, on GitHub.
- `git remote add origin URL` connects your local repository to the remote.
- `git push` sends local commits to the remote.
- `git pull` fetches and integrates remote changes into your current branch.
- Authentication may be required to access a private repository or push changes.

**Remember:** Commit your changes locally first, then push them to GitHub. When you need remote changes on your computer, use pull.