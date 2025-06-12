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
  <img width="700" alt="after git init" src="https://github.com/user-attachments/assets/bef558a7-6adf-4345-964a-018836860486" />
</p>

---

### 📁 The `.git` Folder

After initialization, a hidden `.git` folder is created.

```bash
ls -la
```

<p align="center">
  <img width="700" alt="showing hidden .git folder" src="https://github.com/user-attachments/assets/a9e0a8b9-50a2-4898-af17-cd40b6719c81" />
</p>

I was curious and opened the `.git` folder:

```bash
cd .git
ls
```

<p align="center">
  <img width="700" alt="inside git folder" src="https://github.com/user-attachments/assets/c5fb2da8-e102-4bcf-8941-b76efe6ec810" />
</p>

---

## 🔹 Git Commit and Logs

### ✅ Git Workflow Recap:

```
Working Dir --(git add)--> Staging Area --(git commit)--> Repo --(git push)--> GitHub
```

<p align="center">
  <img width="700" alt="git workflow" src="https://github.com/user-attachments/assets/6e7e0146-7240-4008-84dc-fbbe4de1a5a8" />
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
  <img width="700" alt="untracked files" src="https://github.com/user-attachments/assets/b9fead79-aeb4-455f-86e9-58d237f7d1f0" />
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
  <img width="700" alt="staging status" src="https://github.com/user-attachments/assets/3f663f1f-dd25-4a98-85e0-3481030752c3" />
</p>

---

### 🟢 Committing with Git Commit

I committed the first file:
```bash
git commit -m "add file one"
```

<p align="center">
  <img width="700" alt="commit first file" src="https://github.com/user-attachments/assets/f3a28e64-0304-4613-8175-8b7560f9b71f" />
</p>

Checked `git status` after that and everything was clean.

<p align="center">
  <img width="700" alt="clean status" src="https://github.com/user-attachments/assets/1e6d075d-1ab4-4038-9694-e50e369f8868" />
</p>

---

### 🧾 Git Log

To view commit history:
```bash
git log
git log --oneline
```

<p align="center">
  <img width="700" alt="git log view" src="https://github.com/user-attachments/assets/36de56b5-e67d-475b-9369-b973dbeb8b01" />
</p>
