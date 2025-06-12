## Welcome to my Git & GitHub practice journey! 👋 
This README is a complete walkthrough of everything I’ve learned and practiced—from basic commands to advanced concepts like merge conflicts, stash, and rebase. I’ve documented my experience with real terminal screenshots, Git Graph visuals, and simple explanations to help make concepts easier to understand. Whether you're just starting out with Git or want to brush up on branching, SSH setup, or open-source contribution steps, this guide walks you through it all in a beginner-friendly way. I’ve included examples from my own workflow so it feels more practical than textbook. Hope it helps! 🚀

## 🔹 Git Init and Hidden Folders

### 📝 Side Notes:

- Git is the software, GitHub is a service.
- Version Control System tracks files for changes. Git is a version control system.
- A folder with files is called a **repo** in Git world.
- I checked my git version using:
  ```bash
  git --version
  ```
  Then I updated it using:
  ```bash
  brew install git
  brew upgrade git
  ```

---

### 📁 Folder Setup

I created three folders: `gitone`, `gittwo`, `gitthree`.

Git doesn’t automatically track folders or files unless I initialize it inside that folder.

<p align="center">
  <img width="700" alt="folder creation" src="https://github.com/user-attachments/assets/0b440e69-c0de-44e8-a1e6-8a2af90f341c" />
</p>

---

### ⚠️ Before `git init`

I went into the `gitone` folder and ran:
```bash
git status
```

It gave the error:
```
fatal: not a git repository (or any of the parent directories): .git
```

Which makes sense — Git wasn’t initialized yet.

---

### ✅ After `git init`

I ran:
```bash
git init
```

Now when I run `git status`, it shows:
```
On branch master
No commits yet
```

Only the `gitone` folder is being tracked — not the parent folders.

⚠️ Important: Git must be initialized only once per project, inside the folder you want to track.

<p align="center">
  <img width="668" alt="Pasted Graphic 1" src="https://github.com/user-attachments/assets/fb4de15c-9978-495f-b1f3-6a381fc8a296" />
</p>

---

### 📁 The `.git` Folder

After initialization, a hidden `.git` folder is created.

```bash
ls -la
```

<p align="center">
  <img width="493" alt="drvxr-xr-x 3 sanjanareddy" src="https://github.com/user-attachments/assets/00764ce0-cf47-488b-91c4-ed0912d8d976" />
</p>

I was curious and opened the `.git` folder:

```bash
cd .git
ls
```

<p align="center">
  <img width="783" alt="objects" src="https://github.com/user-attachments/assets/ef8f1b2e-98c5-459c-8667-742a2e20c5f9" />
</p>

---

## 🔹 Git Commit and Logs

### ✅ Git Workflow Recap:

```
Working Dir --(git add)--> Staging Area --(git commit)--> Repo --(git push)--> GitHub
```

<p align="center">
  <img width="547" alt="git commit" src="https://github.com/user-attachments/assets/45078505-20d4-4d8b-b524-877c068a0f3b" />
</p>

---

### 📄 File Creation

I created two text files:
```bash
touch testone.txt texttwo.txt
```

Then ran:
```bash
git status
```

It showed:
```
Untracked files:
  testone.txt
  texttwo.txt
```

<p align="center">
  <img width="624" alt="Githubgitone" src="https://github.com/user-attachments/assets/bff5b52c-6486-463f-aa32-544ae0ca5e25" />
</p>

---

### 🟡 Staging with Git Add

I added only one file:
```bash
git add testone.txt
```

Then checked status again:
```bash
git status
```

Now `testone.txt` is staged, and `texttwo.txt` is still untracked.

<p align="center">
  <img width="558" alt="On branch master" src="https://github.com/user-attachments/assets/548014b6-3665-4647-be97-b181b938e7bc" />
</p>

---

### 🟢 Committing with Git Commit

I committed the first file:
```bash
git commit -m "add file one"
```

<p align="center">
  <img width="608" alt="(aster (Post-cedy) 5366105) rd gite e git commit - add file one" src="https://github.com/user-attachments/assets/a954db6b-191c-4853-b51c-f8f7a2afeabd" />
</p>

Checked `git status` after that and everything was clean.

<p align="center">
  <img width="503" alt="• (base) sanjanareddy@Gs-MacBook-Pro gitone   git status" src="https://github.com/user-attachments/assets/f2b0705d-daaf-4704-a150-a4805bcc22f6" />
</p>

---

### 🧾 Git Log

To view commit history:
```bash
git log
git log --oneline
```

<p align="center">
  <img width="502" alt="commit ca9a5ea9fcedc00e80f096410390d1941958f1f5" src="https://github.com/user-attachments/assets/44401655-09c3-430a-b7d5-ed86ad235457" />
</p>

---

## 🔹 Commit Messages Debate

Commits must be atomic — meaning they should only focus on **one thing at a time**: one feature, one fix, one component.

The official recommendation is to write commit messages in **present tense** and **imperative style**.

Honestly, it feels a little too aggressive to me, but yeah… that’s the standard 😅

---

## 🔹 Git Configuration File

You can check your Git config file using:
```bash
git config --list
```

<p align="center">
  <img width="762" alt="Setting your Git username for every repository on your computer" src="https://github.com/user-attachments/assets/5cb83cd2-000d-4a9e-b686-7279171f94ce" />
</p>

<p align="center">
  <img width="778" alt="Pasted Graphic 13" src="https://github.com/user-attachments/assets/765be578-1f4c-4726-aedd-c9de1f4663fb" />
</p>

---

## 🔹 Git Ignore

All environment variables and sensitive info should be added to `.gitignore`  
This ensures Git **doesn’t track** them accidentally.

<p align="center">
  <img width="591" alt="Untracked files" src="https://github.com/user-attachments/assets/207ce60e-5eba-4401-ad27-4bc1c56cf8a9" />
</p>

In the above image, you can see the `.env` file is being tracked by Git — which we don’t want.

So I added `.env` and other private files into `.gitignore`.

<p align="center">
  <img width="1184" alt="Pasted Graphic 15" src="https://github.com/user-attachments/assets/a31852dd-0e87-46d2-9aeb-b844d44973eb" />
</p>

Now, when I check `git status`, Git is ignoring those files as expected:

<p align="center">
  <img width="668" alt="(base sanjanareddyes-MacBook-Pro gitone A git status" src="https://github.com/user-attachments/assets/45cecd85-af65-435f-8946-1eaaa64b3bbd" />
</p>

I then committed the `.gitignore` file like a normal file:
```bash
git add .gitignore
git commit -m "add gitignore file"
```
---

### 🧠 Side Note

I found out that there are `.gitignore` generators online.  
They suggest what files to ignore based on your tech stack (Node, Python, etc.) — super useful!

<p align="center">
  <img width="1192" alt="Pasted Graphic 17" src="https://github.com/user-attachments/assets/a42f6838-6006-4687-8919-d32a0e182cb1" />
</p>

---

## 🔹 Git Branch

Branches are like alternative timelines 😄  
By default, Git creates a branch called `master` (or sometimes `main`).

<p align="center">
  <img width="485" alt="Pasted Graphic 18" src="https://github.com/user-attachments/assets/7890aec9-3e3d-4d97-a2e1-335c8ccb5d0d" />
</p>

<p align="center">
  <img width="573" alt="• (base)" src="https://github.com/user-attachments/assets/3d3bdde5-4d62-4997-8dda-ce825b4a50f4" />
</p>

We can see we are on the master branch here.

---

## 🔹 Creating Branches

I created a new branch called `nav-bar` using:
```bash
git branch nav-bar
```

Then I checked the branches with:
```bash
git branch
```

And switched to the new one:
```bash
git checkout nav-bar
```

<p align="center">
  <img width="490" alt="sanjanareddy@Gs-MacBook-Pro gittwo   git branch nav-bar" src="https://github.com/user-attachments/assets/383d898b-b047-41e2-bff3-d2c08d5bff90" />
</p>

---

## 🔹 Git Graph Before Working on New Branch

At this point, the `nav-bar` branch was created, but no changes were made to it yet.

<p align="center">
  <img width="898" alt="Pasted Graphic 22" src="https://github.com/user-attachments/assets/10cd283e-a68d-4a26-a4d6-08549d1202d0" />
</p>

---

## 🔹 Committing in the `nav-bar` Branch

I created a new file:
```bash
touch navbar.html
```
Added it and committed:
```bash
git add .
git commit -m "add navbar to code base"
```

<p align="center">
  <img width="891" alt="Pasted Graphic 23" src="https://github.com/user-attachments/assets/504907be-12ce-430b-bf02-1f440bfb3bf8" />
</p>

---

## 🔍 Git Graph After Commit to nav-bar

Now the graph shows that `nav-bar` has progressed beyond `master`.

<p align="center">
  <img width="896" alt="Pasted Graphic 24" src="https://github.com/user-attachments/assets/c1b3c199-cac9-4e9e-8701-218940b84629" />
</p>

---

## 🔁 Switching to Master Branch

Switched to master:
```bash
git checkout master
```

Created a new file:
```bash
touch hero.html
```

Committed the file:
```bash
git add .
git commit -m "add hero section to the code base"
```

<p align="center">
  <img width="1190" alt="Pasted Graphic 27" src="https://github.com/user-attachments/assets/c1995e9d-90a7-464d-9511-ceca92acdeef" />
</p>

---

## 🔍 Git Graph After Both Branches Have Commits

Now `master` has its own new commit, and so does `nav-bar`.  
You can clearly see the diverged paths.

<p align="center">
  <img width="896" alt="Pasted Graphic 28" src="https://github.com/user-attachments/assets/31e87235-c5db-4b46-a150-66caf8742139" />
</p>

---

## 🔁 Switching Between Branches Again

When I’m on `master`, I see only `hero.html`.  
When I switch back to `nav-bar`, I don’t see `hero.html`, but I do see `navbar.html`.

---

## 🔹 Git Log and HEAD

`HEAD` shows the latest commit for the branch you’re currently on.

```bash
git log --oneline
```

This is what it looked like for each branch.

<p align="center">
  <img width="573" alt="Switched to branch" src="https://github.com/user-attachments/assets/919dc713-6247-445f-b445-0a76eec10c75" />
</p>

---

### 🧠 Side Note:

`git switch branch-name` works just like `git checkout branch-name`.  
But `switch` is newer and more readable.

---

## 🔀 Git Merge

I switched back to the `master` branch and merged the `nav-bar` branch:

```bash
git checkout master
git merge nav-bar
```

<p align="center">
 <img width="569" alt="• (base) sanjanareddy@Gs-MacBook-Pro gittwo   git checkout master" src="https://github.com/user-attachments/assets/3e04f5f6-d3cc-4e2a-81cf-4fcbe426f72f" />
</p>

The `++++++++++++` in green means only new lines were added — no deletions. Merge was successful!

Later, I deleted the `nav-bar` branch since it was already merged:

```bash
git branch -d nav-bar
```

---

## 🧠 Git Graph View After Merge

We can see the merge in Git Graph clearly now:

<p align="center">
  <img width="895" alt="Pasted Graphic 31" src="https://github.com/user-attachments/assets/94c6b2da-4167-47a4-a090-971febe3206a" />
</p>

---

## 🔁 Practicing Again with `footer` Branch

I created a new branch called `footer`, made some edits, and merged that too.

<p align="center">
  <img width="893" alt="Pasted Graphic 34" src="https://github.com/user-attachments/assets/c5f29bea-3cbb-4373-b883-bda8686a7277" />
</p>

---

## ⚔️ Git Conflict (Content Conflict)

I edited the same file (`index.html`) from both `master` and `footer` branches.

```bash
git checkout master
# made changes and committed
git checkout footer
# made other changes and committed
```

<p align="center">
  <img width="769" alt="Pasted Graphic 35" src="https://github.com/user-attachments/assets/ff9963ee-819c-48f3-8882-9d1a48823f3f" />

</p>

Then when I tried to merge `footer` into `master`, Git threw a **merge conflict**:

```bash
git merge footer
```

<p align="center">
  <img width="510" alt="(base) sanjanareddy@Gs-MacBook-Pro gittwo   git merge footer" src="https://github.com/user-attachments/assets/ae6c1043-1122-4118-b02f-94ac13191928" />

</p>

---

## 🧩 Resolving Merge Conflicts

Here’s what the conflict looked like inside VS Code:

<p align="center">
  <img width="893" alt="Pasted Graphic 36" src="https://github.com/user-attachments/assets/667957d4-fdf8-45d1-8ba3-9015c40823ef" />

</p>

After editing and resolving the conflict manually, Git asked for a commit to finish the merge.

---

## ✅ Git Graph After Conflict Resolution

Now we can see the new merge commit in Git Graph.

<p align="center">
  <img width="893" alt="Pasted Graphic 38" src="https://github.com/user-attachments/assets/701adf63-3dec-47a0-8947-f4648ebcd2f2" />

</p>

---

## 📊 Git Diff — Comparing File Changes

The `git diff` command shows what changed in a file:

```bash
git diff --staged
```

This compares:
- `a/file.html` (previous version)
- `b/file.html` (new version)

<p align="center">
  <img width="467" alt="(base) sanjanareddy@Gs-MacBook-Pro gittwo   git add" src="https://github.com/user-attachments/assets/dd332025-5313-421b-9629-7938fcc86abf" />

</p>

I also used it on `footer.html` to see specific edits:

<p align="center">
  <img width="587" alt=" Btoster  htal" src="https://github.com/user-attachments/assets/0d86cb4a-05ae-4c82-94ed-b97259334ed0" />

</p>

---

## 🔍 Git Log + Specific Diff Between Commits

To view diff between specific commits, I ran:

```bash
git log --oneline
git diff <commit1> <commit2>
```

This let me check what exactly changed between two points in time.

<p align="center">
  <img width="579" alt="(footer) update index file with footer code" src="https://github.com/user-attachments/assets/ab1906a0-1463-4c0d-99a1-fd5625abab02" />
</p>

---

## Git Stash

Think of `git stash` like a temporary bag where you can keep your current work safely aside, so you can do something else without losing it.

---

Here I created a branch called `bug`, made changes to `footer.html`, but did not stage it. I tried moving to another branch expecting an error so I can stash it — Git didn’t throw an error but told me the file was modified.

<p align="center">
  <img width="541" alt="s to branddy Pos-MacBook-Pro gittwo   git" src="https://github.com/user-attachments/assets/c7329c4f-be08-48ed-be49-36c84f4c0b47" />
</p>

Git allows you to switch branches with uncommitted changes only if:
> The file you changed (`footer.html`) exists in both branches and doesn't conflict between them.

---

Here I made changes to the footer and committed it. I switched to the bug branch, made changes again, but didn't commit. When I tried to go back to footer, Git threw an error because there would be a conflict.

<p align="center">
  <img width="624" alt="• (base) sanjanareddyes MacBook-Pro gitto   git comit -m nake changes to footer" src="https://github.com/user-attachments/assets/04cc09f5-74d8-407e-973d-ac933ee4c73b" />
</p>


---

Now I stashed the changes in the bug branch.

<p align="center">
  <img width="704" alt="ebrorl Yaur loceddranges to ke fogtorin fites cheskoute ovenvritten by checkout" src="https://github.com/user-attachments/assets/7695da90-9705-4e4f-8abf-69ddf50e2d91" />
</p>



---

Here I moved back to the bug branch and popped the stash. My changes were restored to the file.

<p align="center">
  <img width="527" alt="• (base) sanjanareddy@Gs-MacBook-Pro gittwo   git checkout bug" src="https://github.com/user-attachments/assets/af975cbf-a4b5-45ef-aa90-395b7eea5092" />
</p>


---

After finishing the work, I merged all the branches into `master` and the working tree is clean.

<p align="center">
  <img width="589" alt="not restore stater  to discard changes in working directory)" src="https://github.com/user-attachments/assets/1d972c85-c7ca-44b2-92d5-78b1c6b65a91" />
</p>

---

## Stash List

Git allows listing the stash with:

```bash
git stash list
```

<p align="center">
  <img width="659" alt="(base)" src="https://github.com/user-attachments/assets/6d2eb824-8b75-4e83-bf34-f18ed90733a8" />
</p>

---

## Additional Git Commands

### Git Checkout

<p align="center">
  <img width="603" alt="Inex ach foste to footer" src="https://github.com/user-attachments/assets/f3e79018-1a97-4c7a-9081-f61841f8b29f" />
</p>

---

### Git Reflog

<p align="center">
  <img width="802" alt="Pasted Graphic 51" src="https://github.com/user-attachments/assets/eba054bb-7244-4f1e-bd40-a181f066c7c8" />
</p>

## 🔄 Git Rebase

Git rebase is used to:

- Clean up history
- Reapply commits on top of another base tip
- Avoid unnecessary merge commits

📌 **Note**: Never rebase on `main` or `master`. Always do it from a feature or bugfix branch.

---

### 📌 Rebase Diagram

<p align="center">
  <img width="688" alt="Pasted Graphic 52" src="https://github.com/user-attachments/assets/1e3fc947-8a76-492e-a6bd-59882b52de56" />
</p> 

> The top shows a standard merge history with merge commits. The bottom shows a rebased linear history with clean commit sequence.

---

### ✅ Scenario Setup: Commits on master and bug branch

1. Made a commit on `master`: “update main website”
2. Switched to `bug` and committed: “updat navbar”
3. Switched back to `master` and made another commit: “images added”

<p align="center">
  <img width="595" alt="• (base) sanjanareddy@Gs-MacBook-Pro gittwo   git status" src="https://github.com/user-attachments/assets/ac33cdd0-62a5-4738-bc58-1229b54e4d5c" />
</p> 

---

### 🔃 Merging master into bug (Before rebase)

- Switched to `bug`
- Ran `git merge master`

Result:
- Merge completed using `ort` strategy
- `footer.html` and `index.html` had insertions and deletions

<p align="center">
  <img width="478" alt="• (base) sanjanareddy@Gs-MacBook-Pro gittwo   git checkout bug" src="https://github.com/user-attachments/assets/862b0f56-e852-44ef-bc4b-0458fd381dfc" />
</p> 


---

### 🔍 Git Graph Before Rebase

<p align="center">
  <img width="894" alt="Pasted Graphic 55" src="https://github.com/user-attachments/assets/29224cde-8e17-49cd-a774-03147376b0b5" />
</p> 

> You can observe multiple merge lines here — not a clean history.

---

### ⛏️ More Changes on bug and master

- From `bug`, committed another fix
- Switched to `master` again and added more changes

<p align="center">
  <img width="896" alt="Pasted Graphic 56" src="https://github.com/user-attachments/assets/45fbee05-2c4a-4423-8d32-70d5f52ffec2" />
</p> 

---

### 🧹 Performing the Rebase

- Switched to `bug`
- Ran:

```bash
git rebase master
```

Result:
- Rebase successful and history is rewritten

<p align="center">
  <img width="621" alt="buoter" src="https://github.com/user-attachments/assets/6a827b5f-f83d-4da2-836e-02ddd28863af" />
</p>

---

### 📈 Git Graph After Rebase

<p align="center">
  <img width="894" alt="Pasted Graphic 58" src="https://github.com/user-attachments/assets/09173880-180b-4204-b10c-f049eb3c8b79" />
</p>

> Notice: No merge commits. `bug` sits cleanly on top of `master`. This is what rebase gives us — a linear, readable commit history.

---

## 🔐 SSH Keys in GitHub

SSH keys are like a secure, unique signature from your computer that says:
> "Hey GitHub, it’s me! Let me push/pull without typing credentials."

### ✨ Why use SSH keys?

| 🔒 Reason             | ✅ Benefit                                |
|----------------------|--------------------------------------------|
| Secure               | Only your device can access GitHub         |
| Easy                 | No password typing every time              |
| Consistent           | Works even after changing GitHub password |
| Safer than password  | Almost impossible to guess                 |

---

### ⚙️ Setting up SSH (Based on GitHub Docs)

1. Generate SSH key:
   - [Generating SSH key guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

2. (Optional) Add to SSH agent:
   - Useful only if passphrase is set for key
   - Helps avoid retyping passphrase

3. Add key to GitHub:
   - [Add SSH key to GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

---

### 🚀 Pushing Code with SSH

Example commands:
```bash
git remote add origin git@github.com:sanjana459/gitone.git
git push -u origin master
```

<p align="center">
  <img width="755" alt="Pasted Graphic 59" src="https://github.com/user-attachments/assets/6414c975-4039-459d-aede-8f76d643e8e2" />
</p>

---

### 🔁 Git Remote Check

```bash
git remote -v
```

<p align="center">
  <img width="452" alt="git@github comsanjana459gitone-git (fetch)" src="https://github.com/user-attachments/assets/6d1c175a-9a4e-4f88-bad3-8ed83e149cee" />
</p>

---

## 🧑‍💻 Quick Git Reference

| Command              | Purpose                                                              |
|----------------------|----------------------------------------------------------------------|
| `git clone`          | Downloads full repo from GitHub (code + history)                     |
| `git pull`           | Pulls changes from remote and merges                                 |
| `git fetch`          | Downloads changes from remote but doesn’t merge                      |

---

## 🤝 For Open Source Contributions

1. Fork repo
2. Clone forked repo
3. Create new branch (`navbar`)
4. Push changes: `git push origin navbar`
5. Open pull request from `navbar` in your forked repo to the original repo

