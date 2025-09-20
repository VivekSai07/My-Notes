## Make sure the local repo in sync with the remote
```bash
cd ~/ros2_ws/src/Vivek_RobotControl
git fetch origin
git checkout main
git pull origin main
```
This keeps your local repo in sync with the remote.

## Continue your development in ros2_ws/src
```bash
cd ~/ros2_ws
colcon build --packages-select <package-name> --symlink-install
source install/setup.bash
```

### Push updates back to GitHub when ready
```bash
# Go to Vivek_RobotControl and commit
cd ~/ros2_ws/src/Vivek_RobotControl
git add <package-name>
git commit -m "Update <package-name>: <short description of changes>"
git push origin main
```

---

## Add-ons
#### Delete most recent git commit
```bash
git reset --hard HEAD~1
git push origin main --force  # Overwrites the remote main branch history
```

#### Safe Merge (keep both histories)
If you want to preserve commit history from multiple branches:
```bash
# Fetch updates
git fetch origin

# Checkout main locally
git checkout main

# Merge another branch (e.g., previous ros2 work)
git merge <branch-name>
```
- No conflicts → merge completes automatically.
#### Force Replace Main with Another Branch

If you want main to exactly match another branch:
```bash
# Checkout main
git checkout main

# Reset main to match the other branch
git reset --hard <branch-name>

# Push and overwrite remote main
git push origin main --force
```

#### After Merge
1. Future ROS2 work → commit directly to main.
2. Optionally, delete the old branch once everything is merged:
```bash
git branch -d <branch-name>          # delete local
git push origin --delete <branch-name>  # delete remote
```
