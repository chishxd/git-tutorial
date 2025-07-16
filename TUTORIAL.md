# NoteShare Team: Git & GitHub Workflow Tutorial

Welcome to the team! This document is our guide to setting up your developer environment and making code contributions. Follow these steps exactly. We'll be available in the Discord `#dev-setup-help` channel to help if you get stuck.

**Our Goal:** To install Git, connect securely to GitHub using SSH, and then add your name to the `CONTRIBUTORS.md` file using the professional Git workflow.

---

## Part 1: Prerequisites & Setup

This is a one-time setup to get your machine ready.

### Section A: Install Git

First, you need the Git software itself.

*   **For Windows:**
    1.  Go to the official site: [https://git-scm.com/downloads](https://git-scm.com/downloads)
    2.  Download and run the installer.
    3.  During installation, accept the default options for almost everything. The most important thing is to ensure that **Git Bash** is installed. This will give you a powerful terminal for running all the commands below.

*   **For Linux (Fedora/Ubuntu/Debian):**
    Open your terminal and run the command for your distribution:
    *   On Fedora/RedHat: `sudo dnf install git`
    *   On Debian/Ubuntu: `sudo apt-get install git`

### Section B: Configure Git with Your Identity

Open your terminal (use **Git Bash** if you are on Windows) and run the following two commands, replacing the placeholders with your actual name and GitHub email.

```bash
git config --global user.name "Your Full Name"
git config --global user.email "your_email@example.com"
```

### Section C: Set Up an SSH Key for GitHub

We will use SSH keys to connect to GitHub. It's more secure and convenient than using a password every time.

**1. Generate a New SSH Key**
Paste this command into your terminal, replacing the email with your GitHub email.

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
*   When it asks, "Enter a file in which to save the key," just press **Enter** to accept the default location.
*   When it asks, "Enter passphrase," you can either press **Enter** for no passphrase or type a secure password. A passphrase adds an extra layer of security.

**2. Add Your SSH Key to the ssh-agent**
The ssh-agent is a background program that handles your keys.

```bash
# Start the agent in the background
eval "$(ssh-agent -s)"

# Add your new key to the agent
ssh-add ~/.ssh/id_ed25519
```

**3. Add Your Public SSH Key to GitHub**
Now, you need to tell GitHub about your key.

1.  Copy your **public** key to your clipboard. Use the command below. It will print the key to the terminal. Select and copy the entire output.

    ```bash
    cat ~/.ssh/id_ed25519.pub
    ```
    *(For Windows users in Git Bash, if `cat` gives you trouble, you can open the file manually. Go to `C:\Users\YourUser\.ssh\id_ed25519.pub` in File Explorer, open it with Notepad, and copy the contents.)*

2.  Go to your GitHub SSH settings page: [https://github.com/settings/keys](https://github.com/settings/keys)
3.  Click the "**New SSH key**" button.
4.  In the "**Title**" field, give your key a descriptive name (e.g., "My Windows Laptop" or "Fedora Desktop").
5.  In the "**Key**" field, paste the public key you copied.
6.  Click "**Add SSH key**".

**4. Test Your SSH Connection**
Let's verify it all works. Run this command in your terminal:

```bash
ssh -T git@github.com
```
*   You may see a warning like "The authenticity of host 'github.com' can't be established...". This is normal. Type **`yes`** and press Enter.
*   If successful, you will see a message like: `Hi YourUsername! You've successfully authenticated, but GitHub does not provide shell access.` This means you're ready!

---

## Part 2: The Contribution Workflow

Now that setup is done, here's how you will contribute code for every task.

### Step 1: Clone the Repository

Get a copy of the project on your computer. On the GitHub repo page, click the green "Code" button, and make sure to select the **SSH** option. Copy the URL. It should look like `git@github.com:YourTeam/git-bootcamp.git`.

```bash
# Replace the URL with the SSH URL you copied
git clone git@github.com:YourTeam/git-bootcamp.git
```

### Step 2: Create Your Feature Branch

**Never work directly on the `main` branch.** We create a new branch for every task.

```bash
# Move into the newly cloned project directory
cd git-bootcamp

# Create and switch to a new branch. Replace "your-name" with your actual name.
git checkout -b feature/add-your-name
```

### Step 3: Make Your Code Change

1.  Open the `git-bootcamp` folder in VS Code.
2.  Find the file `CONTRIBUTORS.md`.
3.  Add your name on a new line.
4.  Save the file.

### Step 4: Commit Your Change

Save your work to Git's history.

```bash
# 1. Check the status to see your changes
git status

# 2. Add the file to the "staging area"
git add CONTRIBUTORS.md

# 3. Commit the staged file with a clear message
git commit -m "feat: Add [Your Name] to contributors list"
```

### Step 5: Push Your Branch to GitHub

Send your committed changes up to the central GitHub repository.

```bash
# The -u flag links your local branch to the remote one
git push -u origin feature/add-your-name
```

### Step 6: Open a Pull Request (PR)

1.  Go to the `git-bootcamp` repository page on GitHub.
2.  You should see a yellow bar with your branch name. Click the "**Compare & pull request**" button.
3.  **Title:** The title should be clear (e.g., "Add Jane Doe to Contributors").
4.  **Description:** In the description, link the relevant issue (e.g., `Closes #1`).
5.  On the right-hand side, assign a teammate as a "**Reviewer**".
6.  Click "**Create pull request**".

**Congratulations! Your work is now officially submitted for review.**
