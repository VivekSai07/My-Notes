## 1️⃣ Why master exists
- Historically, Git used `master` as the default branch name.
- On older Git versions (and some Windows installs), `git init` still creates master by default.
- Newer Git versions and GitHub default to `main`.

Since you ran `git` init locally, Git created `master`.

## 2️⃣ To make `main` the only branch and remove `master`.
#### Step 1: Delete master on remote
Since your remote only has master and you want main:
```vash
git push origin --delete master
```
This removes the remote `master` branch.
#### Step 2: Rename local master → main
You already ran:
```bash
git branch -M main
```
This is correct — your local branch is now main.

#### Step 3: Push local main to remote and set upstream
Now force push your local main to the empty remote:
```bash
git push -u origin main --force
```

✅ This will:
- Create the main branch on GitHub
- Set it as the upstream for your local main branch
- Remove any conflict with the old master

## 3️⃣ Keep your local repo in sync with the remote
#### Fetch and merge changes from remote
```bash
git fetch origin
git merge origin/main
```
- `git fetch` downloads updates from the remote without changing your working files.
- `git merge` applies any changes from the remote main to your local main.
#### Shortcut: pull (fetch + merge in one step)
```bash
git pull origin main
```
- This is the most common way to keep your local branch up to date.
- It will automatically merge any remote commits into your local branch.

## 4️⃣ Push your local changes to remote
```bash
git add .
git commit -m "Describe your changes"
git push origin main
```

## 5️⃣Undo mistakes and reset your local branch
#### 1. Undo the last commit but keep changes staged
```bash
git reset --soft HEAD~1
```

#### 2. Undo the last commit and unstage changes
```bash
git reset --mixed HEAD~1
```

#### 3. Completely discard last commit (dangerous!)
```bash
git reset --hard HEAD~1
```

> **Warning**: This deletes changes permanently if they weren’t pushed.

#### 4. Reset local branch to match remote main
```bash
git fetch origin
git reset --hard origin/main
```
- Your local branch becomes exactly like the remote.
- Useful if local changes are broken or you want a fresh start.