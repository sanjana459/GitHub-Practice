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
  <img width="894" alt="Pasted Graphic" src="https://github.com/user-attachments/assets/0b440e69-c0de-44e8-a1e6-8a2af90f341c" />
</p>
---

### ⚠️ Before `git init`

Tried `git status` and it gave:
```
fatal: not a git repository (or any of the parent directories): .git
```

<p align="center">
  <img width="668" alt="Pasted Graphic 1" src="https://github.com/user-attachments/assets/60346b90-e0d9-4fdc-8392-6ad0d935f3c0" />
</p>

---

### ✅ After `git init`

Ran:
```bash
git init
```

Now when I run `git status`, it shows I'm on the `master` branch.

Important to note: Only the folder where you initialize git gets tracked.  
So here, only `gitone` is being tracked, not the parent folder.

⚠️ **We initialize Git only once per project.**

<p align="center">
  <img width="493" alt="drvxr-xr-x 3 sanjanareddy" src="https://github.com/user-attachments/assets/452a660b-c792-47e7-9b46-1b43fc305fcc" />
</p>

---

### 📁 The `.git` folder

Once I initialized git, a hidden `.git` folder got created.  
This is where Git keeps history and tracking info.

I got curious and peeked into the `.git` folder — lots of files and subfolders like `config`, `HEAD`, `refs`, etc. 👀

<p align="center">
  <img width="783" alt="objects" src="https://github.com/user-attachments/assets/2258cfe3-1d32-459a-b796-70ecbd562f59" />
</p>

<p align="center">
  <img width="547" alt="git commit" src="https://github.com/user-attachments/assets/cb5c83d7-50eb-405f-ad62-5fd4d6d61553" />
</p>
---

## 🔹 Git Commit and Logs

### ✅ Git Workflow Recap:

```
Working Dir --(git add)--> Staging Area --(git commit)--> Repo --(git push)--> GitHub
```

🖼️ *Screenshot:* Git workflow diagram  
`![Git workflow](images/git-workflow.png)`

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

🖼️ *Screenshot:* Untracked files in git status  
`![Untracked files](images/untracked-files.png)`

---

### 🟡 Staging with Git Add

Ran:
```bash
git add testone.txt
```

Now, `git status` shows `testone.txt` as staged (green), while `texttwo.txt` is still untracked (red).

🖼️ *Screenshot:* One file staged  
`![Staged file](images/file-staged.png)`

---

### 🟢 Committing with Git Commit

Then I committed using:
```bash
git commit -m "add file one"
```

Git shows:
```
1 file changed, 0 insertions(+), 0 deletions(-)
create mode 100644 testone.txt
```

✅ Every commit must have a message.  
Then I added and committed `texttwo.txt`.

🖼️ *Screenshot:* Commit message  
`![Commit one](images/commit-message.png)`

🖼️ *Screenshot:* Clean git status  
`![Clean status](images/clean-status.png)`

---

### 🧾 Git Log

To see the commit history:
```bash
git log
git log --oneline
```

🖼️ *Screenshot:* Git log view  
`![Git log](images/git-log.png)`
