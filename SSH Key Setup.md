## 🔑 Step 1: Check for existing SSH keys

Open CMD/PowerShell and run:
```bash
ls ~/.ssh
```

If you see files like `id_rsa` / `id_ed25519` and their `.pub`, you may already have keys. If not, we’ll create one.

## 🔑 Step 2: Generate a new SSH key

Run:
```bash
ssh-keygen -t ed25519 -C "your_github_email@gmail.com"
```
- Replace with your GitHub email.
- Press Enter to accept the default file location (~/.ssh/id_ed25519).
- Optionally set a passphrase (or leave blank for no passphrase).

## 3. Start ssh-agent service

Run this in CMD/PowerShell (as Administrator):
```bash
Get-Service ssh-agent | Set-Service -StartupType Automatic
Start-Service ssh-agent
```
This makes sure ssh-agent runs automatically every time you log in.

## 4. Add your key
Now add your new key:
```bash
ssh-add $env:USERPROFILE\.ssh\id_ed25519
```

## 5. Verify
Check which keys are loaded:
```bash
ssh-add -l
```
You should see a fingerprint listed.


## 6. Grab your public key
Run this in PowerShell:
```bash
cat $env:USERPROFILE\.ssh\id_ed25519.pub
```

## 7. Add it to GitHub
1. Go to **GitHub → Settings → SSH and GPG Keys → New SSH Key**.
2. Paste the key, give it a name (e.g., Windows Laptop), and save.

## 8. Switch your repo to SSH
1. Create a new repo on GitHub (say mujoco-learning).
2. Back in Terminal:
```bash
git remote add origin git@github.com:YourUsername/mujoco-learning.git

# first push
git add .
git commit -m "Initial commit: setup Mujoco learning repo"
git push -u origin main
```
