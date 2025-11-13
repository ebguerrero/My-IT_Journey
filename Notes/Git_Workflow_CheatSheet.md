# 🐧 Linux Commands Notes – Git Bash Workflow Cheat Sheet

This cheat sheet is for **every time you want to add / update commands** in your `Notes/Linux_Commands.md` file and push the changes to GitHub.

Follow these steps **in order**.

---

## 0. Open Git Bash

Open **Git Bash** and make sure you are in your home directory.

You can check where you are with:

```bash
pwd
```

---

## 1. Go to your repo folder

```bash
cd ~/Documents/My-IT_Journey
```

**What this does:**  
`cd` = *change directory*. This moves you into your Git repository folder so Git can track your changes.

---

## 2. Make sure your local repo is up to date

```bash
git pull
```

**What this does:**  
- Contacts GitHub.  
- Downloads any new commits made online.  
- Merges them into your local copy.  

**Why:**  
Run this before editing so you don’t overwrite newer changes that might be on GitHub.

---

## 3. Edit your Linux commands notes file

```bash
nano Notes/Linux_Commands.md
```

**What this does:**  
Opens the `Linux_Commands.md` file inside the `Notes` folder in the **nano** text editor.

- If the file exists → you edit it.
- If the file doesn’t exist → nano will create it when you save.

**Nano reminders:**

- Type your notes normally.
- `Ctrl + O` → Save (then press **Enter**)
- `Ctrl + X` → Exit nano

---

## 4. See what changed

After you exit nano, run:

```bash
git status
```

**What this does:**  
Shows Git’s view of your repo:

- Which files were modified, added, or deleted
- Whether anything is staged (ready to commit)

You should see something like:

```text
modified: Notes/Linux_Commands.md
```

---

## 5. Stage your notes file (tell Git to track the change)

```bash
git add Notes/Linux_Commands.md
```

**What this does:**  
Moves the file into Git’s **staging area**.

Think of it as:  
> “I want this file included in the next snapshot (commit).”

You can confirm with:

```bash
git status
```

Now you should see:

```text
Changes to be committed:
    modified: Notes/Linux_Commands.md
```

---

## 6. Create a commit (save a snapshot)

```bash
git commit -m "Update Linux commands notes"
```

**What this does:**

- Saves a permanent snapshot of the staged changes.
- Attaches your name + email + message to that snapshot.

**Tips:**

- You can make the message more specific, e.g.:

```bash
git commit -m "Add grep and ss examples to Linux notes"
```

---

## 7. Push your changes to GitHub

```bash
git push
```

**What this does:**

- Sends your local commits to GitHub.
- Updates the repo on the website so it matches your computer.

After this, refresh your GitHub repo page and you’ll see your updated `Linux_Commands.md`.

---

## 8. Verify everything is clean

```bash
git status
```

You should now see:

```text
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

This means:

- All changes are saved.
- All changes are pushed.
- Your local copy and GitHub are in sync.

---

## ⚙️ Quick Reference Table

| Command                                      | Meaning / What it does                                                                 |
|---------------------------------------------|----------------------------------------------------------------------------------------|
| `cd ~/Documents/My-IT_Journey`              | Go into your Git repo folder so Git commands apply to this project.                   |
| `git pull`                                  | Download & merge the latest changes from GitHub into your local repo.                 |
| `nano Notes/Linux_Commands.md`              | Open the Linux commands notes file in the nano text editor.                           |
| `git status`                                | Show which files changed, what’s staged, and repo state.                              |
| `git add Notes/Linux_Commands.md`           | Stage the notes file so it will be included in the next commit.                       |
| `git commit -m "message"`                   | Create a snapshot of staged changes with a short description.                         |
| `git push`                                  | Upload your commits to GitHub so the remote repo is updated.                          |

---

## 🧠 Mental Model

Every time you add a command to your notes, think:

1. **Go to repo** → `cd`
2. **Sync from GitHub** → `git pull`
3. **Edit notes** → `nano`
4. **Check changes** → `git status`
5. **Stage file** → `git add`
6. **Save snapshot** → `git commit`
7. **Upload to GitHub** → `git push`
8. **Confirm clean** → `git status`

Repeat this flow and it will become muscle memory.
