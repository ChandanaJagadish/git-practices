# Day 2: Git Installation and Creating Your First Repository

## 1. Installing Git

Git installation steps depend on your operating system:

- **Windows:** Follow the Windows installation instructions on the official Git website.
- **macOS:** Follow the macOS installation instructions.
- **Linux:** Follow the instructions for your Linux distribution.

You do not need to memorize every installation command; it is enough to know that the steps differ by operating system.

### Verify Git Installation

Open your terminal and run:

```bash
git --version
```

If Git is installed correctly, its version will be displayed. Otherwise, you may see an error saying Git is not recognized or cannot be found.

## 2. Essential Terminal Commands

These commands help you navigate folders and manage files from the terminal.

### 2.1 `pwd` — Print Working Directory

Shows the directory you are currently in.

```bash
pwd
```

**Think:** “Where am I?”

### 2.2 `ls` — List Files and Folders

Shows the files and folders in the current directory.

```bash
ls
```

On Windows, if `ls` is unavailable in your terminal, use:

```cmd
dir
```

**Think:** “What is inside this folder?”

### 2.3 `cd` — Change Directory

Moves you from one directory to another.

```bash
cd Documents
```

Moves into the `Documents` folder, if it exists in the current directory.

```bash
cd ..
```

Moves up one level to the parent directory.

### 2.4 `mkdir` — Make Directory

Creates a new folder.

```bash
mkdir "Newly Created"
```

This creates a folder named `Newly Created` in your current directory.

## 3. What Is a Repository?

A **folder** is a place where you store files. By itself, a normal folder does not keep track of the changes made to those files.

A **Git repository (repo)** is a folder managed by Git. Git can track changes to the files and maintain a history of recorded versions.

**In short:** A folder stores files; a Git repository stores files and uses Git to track their changes over time.

## 4. Create Your First Git Repository

We will turn the `Newly Created` folder into a Git repository.

### Step 1: Navigate into the Folder

```bash
cd "Newly Created"
```

Run this from the directory where you created the folder.

### Step 2: Check What Is Already There

On macOS or Linux:

```bash
ls
```

On Windows Command Prompt:

```cmd
dir
```

Check the existing files before initializing the repository so you know what is already in the project folder.

### Step 3: Create a File (Optional)

On macOS or Linux, create an empty file with:

```bash
touch file1.txt
```

On Windows Command Prompt, use:

```cmd
type nul > file1.txt
```

Both commands create an empty file named `file1.txt`.

### Step 4: Initialize Git

```bash
git init
```

This initializes a new Git repository in the current folder.

### Step 5: Understand the `.git` Directory

Git creates a hidden directory named `.git` when you run `git init`. It contains Git's internal repository data, including configuration and information used to maintain history.

To display hidden files on macOS or Linux:

```bash
ls -a
```

On Windows Command Prompt:

```cmd
dir /a
```

Avoid deleting or manually changing the `.git` directory unless you understand the consequences.

## 5. Check Repository Status

Run:

```bash
git status
```

This displays the current state of the repository, including untracked files, modified files, and changes staged for a commit.

## 6. Quick Revision

| Command | Purpose |
|---|---|
| `git --version` | Check the installed Git version |
| `pwd` | Show the current directory |
| `ls` / `dir` | List files and folders |
| `cd foldername` | Move into a folder |
| `cd ..` | Move to the parent directory |
| `mkdir foldername` | Create a folder |
| `touch file1.txt` | Create a file on macOS/Linux |
| `type nul > file1.txt` | Create a file in Windows Command Prompt |
| `git init` | Initialize a Git repository |
| `git status` | Check the repository's current state |

## Learning Tip

After the lesson, practise these commands yourself. Research any command you do not fully understand and ask questions to learn more about how it works.
