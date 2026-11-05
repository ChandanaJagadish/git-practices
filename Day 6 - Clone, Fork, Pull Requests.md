# Day 6: Git and GitHub — Clone, Fork and Pull Request

## 1. Introduction: Open Source Contribution

Open-source contribution means contributing to projects developed and maintained by other people.

You can explore an existing project, understand its code, add new features, fix bugs, and propose your changes to the project maintainers.

**Important:** You cannot automatically contribute changes to every repository. You can explore public repositories, but contributing changes to the original repository depends on its contribution guidelines and permissions. Usually, contributors use the Fork and Pull Request workflow.

## 2. What Is Git Clone?

**Git Clone** means creating a local copy of an existing remote repository on your computer.

For example, GitHub contains many public repositories. You can clone these repositories onto your local system, open them in your code editor, understand the project, and work on them.

### Practical Example: Clone a Repository

1. Visit GitHub.
2. Search for `first-contributions`.
3. Open the repository.
4. Click the green **Code** button.
5. Select **HTTPS**.
6. Copy the repository URL.

Open your terminal and navigate to the location where you want to store the project.

```bash
cd Documents
```

Clone the repository:

```bash
git clone https://github.com/OWNER/REPOSITORY.git
```

Replace the example URL with the actual URL you copied.

Enter the cloned folder:

```bash
cd REPOSITORY
```

The repository is now available on your local computer.

**Important:** You do not need to run `git init` before cloning. Git Clone automatically creates the local repository and its `.git` directory.

## 3. What Is Fork?

**Fork** means creating your own copy of someone else's repository under your GitHub account.

For example, imagine there is an open-source repository called `first-contributions`.

When you click the **Fork** option at the top of that repository, GitHub creates a copy of the project under your own GitHub account.

This allows you to work on the project without directly changing the original repository.

### How Does Fork Work?

Consider this sequence:

1. An original open-source repository called `first-contributions` exists on GitHub.
2. You click **Fork** on that repository.
3. A copy of the entire repository is created under your GitHub account.
4. You can now clone your forked repository onto your laptop and work on it.

In simple words:

- **Fork:** Creates a copy of someone else's repository in your GitHub account.
- **Clone:** Downloads a repository onto your local computer.

## 4. Difference Between Fork and Clone

| Fork | Clone |
|---|---|
| Creates a copy under your GitHub account. | Creates a local copy on your computer. |
| Happens on GitHub. | Happens on your local system. |
| Gives you your own remote repository to work with. | Allows you to work with project files locally. |

### Remember the Order

**Original Repository → Fork → Your GitHub Repository → Clone → Your Local Computer**

## 5. Complete Open Source Contribution Workflow

Now let's understand how you can contribute changes to someone else's project.

### Step 1: Fork the Original Repository

Visit the original open-source repository and click the **Fork** option.

GitHub creates a copy of that repository under your account.

### Step 2: Clone Your Forked Repository

Open your forked repository on GitHub.

1. Click the green **Code** button.
2. Select **HTTPS**.
3. Copy the repository URL.

Open your terminal and run:

```bash
git clone YOUR_FORKED_REPOSITORY_URL
```

Your forked repository is now available on your laptop.

### Step 3: Make Changes to the Project

Open the cloned project in your code editor.

You can now:
- Add a new feature.
- Fix an existing bug.
- Improve the code.
- Make other changes according to the project's contribution guidelines.

### Step 4: Create a Separate Branch (Recommended)

Instead of directly making changes on the `main` branch, create a separate branch.

```bash
git switch -c feature-login
```

This creates a new branch and switches you to it.

### Step 5: Stage and Commit Your Changes

After making changes, check the repository status:

```bash
git status
```

Stage your changes:

```bash
git add .
```

Commit them:

```bash
git commit -m "Add login feature"
```

### Step 6: Push Your Changes

Push your branch to your forked repository on GitHub:

```bash
git push -u origin feature-login
```

Here:
- `git push` uploads your commits.
- `origin` refers to your forked repository.
- `feature-login` is the branch you are pushing.

**Important:** At this stage, your changes are uploaded only to your forked repository. The original repository has not been changed.

## 6. What Is a Pull Request (PR)?

A **Pull Request (PR)** is a request to the original repository's maintainers to review and potentially merge your changes into their project.

Think of it this way:

You have made some changes to an open-source project. Now you want the original project owner to include those changes in their repository.

You raise a Pull Request to communicate:

"I have made these changes to your project. Could you please review them and consider merging them?"

### Why Do We Need Pull Requests?

Open-source projects are generally maintained by specific owners or maintainers.

They do not automatically accept every contribution because they need to ensure that:

- The code works correctly.
- The changes follow the project's coding standards.
- The changes do not introduce bugs.
- The contribution is useful to the project.

Therefore, maintainers review Pull Requests before merging them.

## 7. How to Create a Pull Request

After pushing your changes to your forked repository:

### Step 1: Open Your Forked Repository

Visit your forked repository on GitHub.

### Step 2: Find the Contribute Option

On your forked repository's page, you may see a **Contribute** option.

Click it.

### Step 3: Open a Pull Request

Select **Open pull request**.

GitHub will allow you to compare your branch with the corresponding branch of the original repository.

Check that:

- **Base repository:** The original repository.
- **Base branch:** The branch into which you want your changes merged, usually `main`.
- **Head repository:** Your forked repository.
- **Compare branch:** Your feature branch, such as `feature-login`.

### Step 4: Submit the Pull Request

Provide:
- A suitable Pull Request title.
- A description of the changes you made.
- Any relevant details requested by the project.

Click **Create pull request**.

Your Pull Request is now submitted to the original repository.

## 8. What Happens After Creating a Pull Request?

Once you open a Pull Request:

1. The original repository's maintainers review your changes.
2. They may approve the changes.
3. They may request modifications if something needs improvement.
4. You can make the requested changes, commit them, and push them to the same branch.
5. Once the maintainers are satisfied, they can merge the Pull Request.

**Remember:** Creating a Pull Request does not automatically merge your changes. The repository maintainers decide whether to accept and merge them.

## 9. Complete Open Source Contribution Workflow — Quick Revision

```text
Original Open Source Repository
              |
              v
          Fork Repo
              |
              v
     Your GitHub Repository
              |
              v
          Clone Repo
              |
              v
       Local Repository
              |
              v
       Create a Branch
              |
              v
       Make Code Changes
              |
              v
        git add .
              |
              v
         git commit
              |
              v
         git push
              |
              v
      Your Forked Repository
              |
              v
      Create Pull Request
              |
              v
       Maintainer Review
              |
              v
       PR Approved & Merged
              |
              v
      Original Repository
```

## 10. Important Commands — Quick Revision

| Command | Purpose |
|---|---|
| `git clone URL` | Clone a remote repository |
| `git switch -c branch-name` | Create and switch to a branch |
| `git status` | Check the status of files |
| `git add .` | Stage changes |
| `git commit -m "message"` | Commit staged changes |
| `git push -u origin branch-name` | Push a branch to your fork |
| `git pull` | Fetch and integrate remote changes |

## 11. Key Takeaways

- **Clone:** Download an existing repository to your local computer.
- **Fork:** Create your own copy of someone else's repository on GitHub.
- **Branch:** Create an independent line of development.
- **Push:** Upload your local commits to your remote repository.
- **Pull Request:** Ask the original repository's maintainers to review and potentially merge your changes.
- **Code Review:** Maintainers examine your changes before accepting them.

**Remember the main workflow:**

**Fork → Clone → Create Branch → Make Changes → Add → Commit → Push → Pull Request → Review → Merge**

This workflow is widely used in open-source projects and professional software development teams.