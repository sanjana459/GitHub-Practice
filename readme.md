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


