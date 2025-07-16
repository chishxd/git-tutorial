# NoteShare Team: Git & GitHub Workflow Tutorial

Welcome to the team! This document is our guide to making code contributions. Follow these steps exactly. We'll do this together in the Discord `#dev-setup-help` channel.

**Our Goal:** To add your name to the `CONTRIBUTORS.md` file using the professional Git workflow.

---

### Step 1: Clone the Repository

First, get a copy of the project on your computer. Open your terminal (Git Bash on Windows) and run this command. Make sure you're in a directory where you want to store your projects (like `C:\Users\YourUser\dev`):

```bash
git clone <paste_the_https_clone_url_of_the_git-bootcamp_repo_here>
```

---

### Step 2: Create Your Feature Branch

**Never work directly on the `main` branch.** We create a new branch for every task. This keeps `main` clean. Your branch name should be descriptive.

Run these commands:
```bash
# Move into the newly cloned project directory
cd git-bootcamp

# Create and switch to a new branch. Replace "your-name" with your actual name.
git checkout -b feature/add-your-name
```

---

### Step 3: Make Your Code Change

1.  Open the `git-bootcamp` folder in VS Code.
2.  Find the file `CONTRIBUTORS.md`.
3.  Add your name on a new line.
4.  Save the file.

---

### Step 4: Commit Your Change

Now we save your work to Git's history. This is a two-step process.

```bash
# 1. Check the status to see what you've changed
git status

# 2. Add the file to the "staging area"
git add CONTRIBUTORS.md

# 3. Commit the staged file with a clear message
git commit -m "feat: Add [Your Name] to contributors list"
```
*(Note: "feat:" is a convention meaning we're adding a new feature.)*

---

### Step 5: Push Your Branch to GitHub

Your commit is currently only on your machine. Let's push it to the central GitHub repository so others can see it.

```bash
# The -u flag links your local branch to the remote one
git push -u origin feature/add-your-name
```

---

### Step 6: Open a Pull Request (PR)

1.  Go to the `git-bootcamp` repository page on GitHub in your browser.
2.  You should see a yellow bar with your branch name. Click the "Compare & pull request" button.
3.  **Title:** The title should be clear (e.g., "Add Jane Doe to Contributors").
4.  **Description:** In the description, type `Closes #1`. (We will create an issue #1 for this task).
5.  On the right-hand side, assign your team lead as a "Reviewer".
6.  Click "Create pull request".

**You're done! Your work is now ready for review.**
