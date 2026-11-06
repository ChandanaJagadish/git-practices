# Day 8 – Getting Inside the IDE (VS Code)

An IDE (Integrated Development Environment) provides tools to write, edit, run, and manage code. VS Code is a popular code editor that also provides Git integration.

Traditionally, developers used the command-line interface (CLI) to perform Git operations. Even today, using Git through the CLI is a powerful and reliable approach. However, many developers also use IDEs such as Visual Studio Code (VS Code) to perform Git operations through a graphical interface.

In VS Code, Git features are available through the Source Control panel. You can also install extensions to get additional features, such as visualizing commit history and branches through a Git graph.

Today, we will learn how to perform operations such as creating commits, pushing, pulling, merging branches, and connecting GitHub—all through VS Code without typing Git commands.

## 1. Create a Folder and Open It in VS Code

1. Create a folder in any location you prefer.
2. Open VS Code.
3. Go to File → Open Folder and select the folder you created.

## 2. Install Git Extensions

1. Open the Extensions panel from the left sidebar.
2. Search for Git-related extensions.
3. Install the extension you want.

Note: VS Code already has built-in Git support. You do not need to install an extension just to perform basic Git operations. However, extensions such as Git Graph provide a visual representation of commits and branches.

You must also have Git installed on your computer.

## 3. Convert the Folder into a Git Repository

Before tracking files, you need to initialize Git in your folder.

1. Open the Source Control panel from the left sidebar. It has a branch-like icon.
2. You may see an option called Initialize Repository.
3. Click it.

That's it! Your folder is now a Git repository.

This is equivalent to running:

```
git init
```

You are now working inside a Git version-controlled repository. Initially, you will be on the `main` branch (depending on your Git configuration).

## 4. Create a File and Check Its Status

1. Create a new file inside your folder, such as `index.html`.
2. Open the Source Control panel.
3. You will see the newly created file listed under Changes.

You may notice the letter `U` beside the file.

- U – Untracked: Git has detected the file, but it is not yet being tracked.
- M – Modified: An already tracked file has been changed.
- A – Added: A new file has been staged.

## 5. Stage a File Using VS Code

In the command line, we use:

```
git add index.html
```

In VS Code, you can perform the same operation without typing the command.

1. Go to the Source Control panel.
2. Find your file under Changes.
3. Click the + (Plus) icon beside the file.

Once you click the plus icon, the file moves to Staged Changes.

This means you have successfully staged the file, just like using `git add`.

## 6. Commit Changes Using VS Code

After staging the file, the next step is to commit it.

1. Go to the message box at the top of the Source Control panel.
2. Enter a commit message, such as:

   `Add index.html`
3. Click Commit.

This is equivalent to running:

```
git commit -m "Add index.html"
```

Your changes are now committed to your local Git repository.

## 7. Create a Branch Using VS Code

Before pushing and pulling, let's understand how to create a branch.

At the bottom-left corner of VS Code, you can see the name of your current branch, usually `main`.

1. Click the current branch name.
2. Select Create New Branch.
3. Enter a branch name, such as `feature-login`.
4. Press Enter.

VS Code creates the branch and switches you to it.

This is equivalent to:

```
git switch -c feature-login
```

You can also switch between branches by clicking the branch name and selecting the branch you want.

## 8. Publish a Branch

After creating a branch, you may see an option called Publish Branch in the Source Control panel.

Click it to publish your local branch to the remote GitHub repository.

This is equivalent to pushing the branch to GitHub for the first time.

## 9. Connect Your Repository to GitHub

If your local repository is not connected to GitHub, you need to publish it or add a remote repository.

VS Code provides an option such as Publish to GitHub.

1. Open the Source Control panel.
2. Select Publish to GitHub if available.
3. Sign in to your GitHub account when prompted.
4. Choose whether the repository should be Public or Private.
5. Follow the prompts to publish it.

- Public repository: Anyone can view the repository.
- Private repository: Only you and people you grant access to can view it.

## 10. Sync Changes

After connecting your local repository to GitHub, you may see an option called Sync Changes.

Sync Changes helps synchronize your local branch with its remote counterpart.

It generally performs:

- Push: Sends your local commits to GitHub.
- Pull: Fetches and integrates changes from GitHub into your local branch.

For example, if you modify a file, stage it, and commit it, you can use Sync Changes to push your changes to GitHub.

## 11. Explore More Git Operations

In the Source Control panel, you can also find a three-dot menu (`...`).

Click it to explore additional Git operations, such as:

- Push
- Pull
- Fetch
- Branch operations
- Merge
- Stash

The exact options may vary depending on your VS Code version, extensions, and repository setup.

Day 8 takeaway: You can perform most common Git operations through VS Code's graphical interface instead of typing commands in the terminal. However, the underlying Git operations remain the same.