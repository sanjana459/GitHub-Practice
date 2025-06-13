## Welcome to my Git & GitHub practice journey 👋

Hi! This is a small guide I made while learning Git and GitHub. I’ve included everything I tried myself—like making branches, merging, resolving conflicts, using stash, rebase, and pushing code to GitHub using SSH keys. I also added screenshots I took on my own laptop, so it’s easier to follow along. While this is mainly for my own learning, I hope it helps anyone else who's getting started too. I’ve tried to keep the explanations simple and beginner-friendly.

## Git Init and Hidden Folders

### Quick Notes

Here’s what I understood while getting started:  
• Git is the actual software. GitHub is the hosting service.  
• Git is a version control system that tracks your file changes.  
• A folder with files is what Git refers to as a “repo.”  
• I checked my Git version by running this:

```bash
git --version
```

To update it, I ran:

```bash
brew install git
brew upgrade git
```

---

### Creating My Folder Structure

I made three folders: `gitone`, `gittwo`, and `gitthree`.

Git won’t start tracking anything unless you initialize it inside one of these folders.

<p align="center">
  <img width="700" alt="folder creation" src="https://github.com/user-attachments/assets/0b440e69-c0de-44e8-a1e6-8a2af90f341c" />
</p>

---

### What Happens Before Running `git init`

Inside the `gitone` folder, I tried checking the Git status:

```bash
git status
```

But got this message:

```
fatal: not a git repository (or any of the parent directories): .git
```

Which made sense—Git wasn’t set up there yet.

---

### Initializing Git

I ran the init command:

```bash
git init
```

After that, `git status` showed:

```
On branch master
No commits yet
```

This confirmed that Git started tracking `gitone` only. The folders outside it remain untouched.

💡 Just a reminder to myself: You should only run `git init` once per project.

<p align="center">
  <img width="668" alt="Pasted Graphic 1" src="https://github.com/user-attachments/assets/fb4de15c-9978-495f-b1f3-6a381fc8a296" />
</p>

---

### Exploring the `.git` Folder

Once Git was initialized, a hidden `.git` folder appeared.

I used:

```bash
ls -la
```

Then I opened it using:

```bash
cd .git
ls
```

<p align="center">
  <img width="783" alt="objects" src="https://github.com/user-attachments/assets/ef8f1b2e-98c5-459c-8667-742a2e20c5f9" />
</p>

---

## Git Commit and Logs

### Workflow Summary

This is how I understood Git’s flow:

```
Working Directory → Staging Area → Local Repository → GitHub
```

Use `git add` to move files to staging, then `git commit`, and finally `git push` to send changes to GitHub.

<p align="center">
  <img width="547" alt="git commit" src="https://github.com/user-attachments/assets/45078505-20d4-4d8b-b524-877c068a0f3b" />
</p>

---

### Creating and Tracking Files

I created two files using:

```bash
touch testone.txt texttwo.txt
```

Then checked their status:

```bash
git status
```

Git listed them as untracked.

<p align="center">
  <img width="624" alt="Githubgitone" src="https://github.com/user-attachments/assets/bff5b52c-6486-463f-aa32-544ae0ca5e25" />
</p>

---

### Staging a File

I added just one file to the staging area:

```bash
git add testone.txt
```

When I checked status again, one file was staged while the other remained untracked.

<p align="center">
  <img width="558" alt="On branch master" src="https://github.com/user-attachments/assets/548014b6-3665-4647-be97-b181b938e7bc" />
</p>

---

### Committing Changes

I committed the staged file using:

```bash
git commit -m "add file one"
```

<p align="center">
  <img width="608" alt="git commit" src="https://github.com/user-attachments/assets/a954db6b-191c-4853-b51c-f8f7a2afeabd" />
</p>

Status now showed everything was committed.

<p align="center">
  <img width="503" alt="git status" src="https://github.com/user-attachments/assets/f2b0705d-daaf-4704-a150-a4805bcc22f6" />
</p>

---

### Checking Commit Logs

To view commit history, I used:

```bash
git log
git log --oneline
```

<p align="center">
  <img width="502" alt="git log" src="https://github.com/user-attachments/assets/44401655-09c3-430a-b7d5-ed86ad235457" />
</p>

---

## Writing Good Commit Messages

I learned that commits should be small and focused on a single change—one file, one fix, one feature.

Best practice is to write them in present tense like:
```
Add footer section
Fix nav bug
Update hero image
```

Even if it feels a bit aggressive, this is the convention developers follow.

---

## Git Configuration

To see your Git setup, run:

```bash
git config --list
```

<p align="center">
  <img width="762" alt="git config list" src="https://github.com/user-attachments/assets/5cb83cd2-000d-4a9e-b686-7279171f94ce" />
</p>

---

## Git Ignore

If there are sensitive files like `.env` or folders like `node_modules`, they should be added to a `.gitignore` file. Git won’t track them.

<p align="center">
  <img width="591" alt="Untracked files" src="https://github.com/user-attachments/assets/207ce60e-5eba-4401-ad27-4bc1c56cf8a9" />
</p>

After adding `.env` to `.gitignore`, Git stopped showing it in `git status`.

<p align="center">
  <img width="668" alt="git status clean" src="https://github.com/user-attachments/assets/45cecd85-af65-435f-8946-1eaaa64b3bbd" />
</p>

Then I committed the `.gitignore` file itself.

```bash
git add .gitignore
git commit -m "add gitignore file"
```

---


## Git Branch

A branch in Git is like creating a parallel timeline where you can work on something new without touching the main work. Git creates a default branch called `master` (sometimes it’s `main`).

<p align="center">
  <img width="485" alt="Pasted Graphic 18" src="https://github.com/user-attachments/assets/7890aec9-3e3d-4d97-a2e1-335c8ccb5d0d" />
</p>

<p align="center">
  <img width="573" alt="• (base)" src="https://github.com/user-attachments/assets/3d3bdde5-4d62-4997-8dda-ce825b4a50f4" />
</p>

---

## Creating a Branch

I made a new branch called `nav-bar` like this:

```bash
git branch nav-bar
```

To see the list of branches:

```bash
git branch
```

And then I switched to the new branch:

```bash
git checkout nav-bar
```

<p align="center">
  <img width="490" alt="branch nav-bar" src="https://github.com/user-attachments/assets/383d898b-b047-41e2-bff3-d2c08d5bff90" />
</p>

---

## Viewing Branch Progress in Git Graph

At this stage, both branches existed, but only `nav-bar` had new commits.

<p align="center">
  <img width="898" alt="Pasted Graphic 22" src="https://github.com/user-attachments/assets/10cd283e-a68d-4a26-a4d6-08549d1202d0" />
</p>

---

## Making Commits in a Branch

Inside the `nav-bar` branch, I created a new file:

```bash
touch navbar.html
```

Then I added and committed the change:

```bash
git add .
git commit -m "add navbar to code base"
```

<p align="center">
  <img width="891" alt="Pasted Graphic 23" src="https://github.com/user-attachments/assets/504907be-12ce-430b-bf02-1f440bfb3bf8" />
</p>

---

## Switching to Another Branch

I went back to the `master` branch:

```bash
git checkout master
```

Then I added a new file:

```bash
touch hero.html
```

And committed it:

```bash
git add .
git commit -m "add hero section to the code base"
```

<p align="center">
  <img width="1190" alt="Pasted Graphic 27" src="https://github.com/user-attachments/assets/c1995e9d-90a7-464d-9511-ceca92acdeef" />
</p>

---

## Visualizing Diverged Branches

Now both branches had their own unique commits.

<p align="center">
  <img width="896" alt="Pasted Graphic 28" src="https://github.com/user-attachments/assets/31e87235-c5db-4b46-a150-66caf8742139" />
</p>

---

## Switching Between Branches

Each branch shows its own committed files. `master` had `hero.html`, and `nav-bar` had `navbar.html`.

---

## Git Log and HEAD

The `HEAD` pointer shows the latest commit for the current branch. You can check:

```bash
git log --oneline
```

<p align="center">
  <img width="573" alt="Switched to branch" src="https://github.com/user-attachments/assets/919dc713-6247-445f-b445-0a76eec10c75" />
</p>

---

## Git Merge

To combine changes from another branch into the current one, I used:

```bash
git checkout master
git merge nav-bar
```

<p align="center">
 <img width="569" alt="git merge nav-bar" src="https://github.com/user-attachments/assets/3e04f5f6-d3cc-4e2a-81cf-4fcbe426f72f" />
</p>

After merging, I deleted the branch:

```bash
git branch -d nav-bar
```

<p align="center">
  <img width="895" alt="Pasted Graphic 31" src="https://github.com/user-attachments/assets/94c6b2da-4167-47a4-a090-971febe3206a" />
</p>

---

## Handling Merge Conflicts

If both branches edited the same part of a file, Git will pause and ask you to resolve the conflict.

<p align="center">
  <img width="769" alt="Pasted Graphic 35" src="https://github.com/user-attachments/assets/ff9963ee-819c-48f3-8882-9d1a48823f3f" />
</p>

Conflict looks like this:

```html
<<<<<<< HEAD
content from master
=======
content from feature branch
>>>>>>> branch-name
```

I manually chose what to keep and removed those conflict markers. Then committed again.

<p align="center">
  <img width="893" alt="Pasted Graphic 36" src="https://github.com/user-attachments/assets/667957d4-fdf8-45d1-8ba3-9015c40823ef" />
</p>

---

## Git Diff

To compare staged changes:

```bash
git diff --staged
```

<p align="center">
  <img width="467" alt="git diff" src="https://github.com/user-attachments/assets/dd332025-5313-421b-9629-7938fcc86abf" />
</p>

You can also check differences between two commits:

```bash
git log --oneline
git diff <commit1> <commit2>
```

---

## Git Stash

When you need to pause work and switch tasks but aren’t ready to commit, stash is useful:

```bash
git stash
```

It saves your current changes and cleans up the working directory.

```bash
git stash list
git stash pop
```

<p align="center">
  <img width="704" alt="stash" src="https://github.com/user-attachments/assets/7695da90-9705-4e4f-8abf-69ddf50e2d91" />
</p>

---

## Git Rebase

Rebase helps clean up commit history by stacking commits in a linear order.

📌 Do not use `rebase` on the `main` or `master` branch directly.

```bash
git rebase master
```

This replays your changes from the feature branch as if they were added after the latest `master` commit.

<p align="center">
  <img width="894" alt="Pasted Graphic 58" src="https://github.com/user-attachments/assets/09173880-180b-4204-b10c-f049eb3c8b79" />
</p>

Now the graph is clean—no extra merge commits.

---

## Setting Up SSH with GitHub

SSH lets you push code without entering your password every time.

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Then add your public key to GitHub settings under SSH keys.

To connect:

```bash
git remote add origin git@github.com:yourusername/yourrepo.git
git push -u origin master
```

<p align="center">
  <img width="755" alt="SSH" src="https://github.com/user-attachments/assets/6414c975-4039-459d-aede-8f76d643e8e2" />
</p>

---

## Useful Git Commands Summary

| Command            | What It Does                                              |
|--------------------|-----------------------------------------------------------|
| `git clone`        | Copy a repo from GitHub to your computer                  |
| `git pull`         | Bring latest changes from GitHub into your local project |
| `git push`         | Upload your local changes to GitHub                      |
| `git checkout`     | Switch between branches                                  |
| `git branch`       | View or create branches                                  |
| `git stash`        | Temporarily save uncommitted changes                     |
| `git rebase`       | Clean up commit history                                  |

---

## Open Source Contribution Flow

If you're contributing to someone else's GitHub repo:

1. Fork their repository
2. Clone your fork
3. Create a branch for your changes
4. Make edits and push to your branch
5. Open a pull request to the original repo

---

## Final Words

Everything here is what I practiced myself. I made sure to try the commands and take screenshots so I could remember things better later.

If you’re just starting out with Git, I hope this guide helped you see things clearly. Thanks for reading!

