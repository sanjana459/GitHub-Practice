## 🔹 Git Init and Hidden Folders

I am going to read some theory and also practice it on a file in VS Code.

---

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
