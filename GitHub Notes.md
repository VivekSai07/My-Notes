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