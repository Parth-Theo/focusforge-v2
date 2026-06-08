# Security Cleanup Guide for FocusForge

## Issue: Passwords Committed to Git History

Real passwords were accidentally committed in an earlier version. Even after deletion, they remain in git history and can be recovered.

## Solution: Purge Git History

### Option 1: Delete and Recreate Repo (Recommended)

1. **Download your code** (without .git folder):
   ```bash
   git clone https://github.com/Parth-Theo/focusforge.git temp-folder
   rm -rf temp-folder/.git
   ```

2. **Create a new repo** with a fresh history:
   - Go to GitHub → Settings → Danger Zone → Delete this repository
   - Create a new empty repo with the same name
   - Push your cleaned code

3. **Tell affected users to change passwords** reused elsewhere

### Option 2: Filter History (Advanced)

```bash
# Install git filter-repo
pip install git-filter-repo

# Clone the repo
git clone --bare https://github.com/Parth-Theo/focusforge.git

# Remove sensitive files
git filter-repo --path-glob '*.csv' --invert-paths
git filter-repo --path-glob '*users*' --invert-paths

# Push cleaned history
git push --force origin main
```

## Verification

After cleanup, verify no secrets remain:
```bash
git log --all -p | grep -iE "password|secret" | head -20
```

## Prevention

1. Always use `.gitignore` for sensitive files
2. Never commit real credentials to version control
3. Use environment variables for secrets in production
4. Enable GitHub Secret Scanning on the repo
