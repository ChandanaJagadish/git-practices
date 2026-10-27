# Day 3: Git Configuration and the Commit Cycle
## 1. Setting Your Git Username and Email
Before making commits, configure your Git username and email. This information identifies the author associated with your commits.
Set Your Username
git config --global user.name "Your Name"
Replace Your Name with your actual name.
Set Your Email
git config --global user.email "your@email.com"
Replace your@email.com with your email address.

The --global option applies these settings to your Git repositories by default for your current user account.
## 2. Introduction to the Git Commit Cycle
The commit cycle is one of the most important concepts in Git.
### 2.1 What Is a Commit?
Think of a commit as a decision to record a set of changes in your project.

Imagine a relationship in which a new person enters your life. You might consider how your life has changed since that person's arrival. Similarly, when you make changes to a project, you can examine how the project has changed compared with its previous state.

In Git, a commit records a snapshot of your project at a particular point in time, along with a message describing the changes made.

For example, imagine you are building a website:
1. First commit: Create the homepage.
2. Second commit: Improve the homepage layout.
3. Third commit: Fix an issue in the homepage layout.
Each commit records a specific set of changes and includes a short message explaining what was done.

This allows you to track the project's progress and understand what changed between different versions. You can also return to an earlier state when necessary.
### 2.2 The Three Main Steps of the Commit Cycle
The basic commit workflow involves three important commands:
1. git status
2. git add
3. git commit
Step 1: git status
Checks the current state of your working directory and shows which files have been modified, are untracked, or are staged.
Step 2: git add — Staging Area
When you modify files in your working directory, those changes are not automatically included in a commit.

You use git add to select the changes you want to include in the next commit.

For example:
git add index.html
This stages the changes to index.html.

The staging area is like a preparation area in a military operation. Before proceeding, the necessary people and equipment are gathered and checked.

Similarly, in Git, you select only the changes you want to include in the next commit and prepare them for recording. You do not have to stage every changed file.
Step 3: git commit — Record the Changes
Once you have checked the staged changes, you can record them in the repository.
git commit -m "Create homepage"
The -m option lets you provide a short message describing the changes.

A commit records the staged changes as a new snapshot in your project's history.
Commit Cycle Summary
Working Directory → Staging Area → Repository
- Working directory: Make changes to your files.
- Staging area: Select the changes you want to include using git add.
- Repository: Record those staged changes using git commit.
The git status command helps you check the state of your files throughout this process.