# GitHub Playbook – Local to Remote (Repeatable Steps)

This playbook is for setting up, pushing, and maintaining a GitHub repository from a local machine.

---

## 0) One-time setup (set your Git identity)

These tell Git who you are (must match your GitHub account email):

git config --global user.name "Your Name"
git config --global user.email "your_github_email@example.com"

---

## 1) Create your project structure

mkdir icecream-ml && cd icecream-ml
# Add your files/folders:
# .gitignore, README.md, scripts/, data/, outputs/, notebooks/

---

## 2) Initialize Git

git init
git add .
git commit -m "Initial commit: project setup"

---

## 3) Create an empty repo on GitHub

1. Go to github.com → New repository
2. Name it (e.g., icecream-ml)
3. Leave it empty (do not add README/license online)

---

## 4) Connect local repo to remote + push to main

git remote add origin https://github.com/<USERNAME>/icecream-ml.git
git branch -M main
git push -u origin main

---

## 5) Daily workflow (after making changes)

git status                           # check changes
git add scripts/forecast_icecream.py # stage file(s)
git commit -m "Add forecast script with weather"
git push                             # push to GitHub

---

## 6) Before you start working (avoid conflicts)

git pull

---

## 7) Share your Conda environment (optional but recommended)

conda env export > environment.yml
git add environment.yml
git commit -m "Add environment spec"
git push

---

## 8) Common fixes & checks

- Check remote URL:
  git remote -v

- Replace wrong remote URL:
  git remote remove origin
  git remote add origin https://github.com/<USERNAME>/<REPO>.git

- Fix "author identity unknown":
  git config --global user.name "Your Name"
  git config --global user.email "your_github_email@example.com"

- Fix "no upstream branch" error:
  git push -u origin main

---

## 9) Optional: SSH keys (no more passwords)

ssh-keygen -t ed25519 -C "your_github_email@example.com"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
# Add the public key to GitHub → Settings → SSH and GPG keys
git remote set-url origin git@github.com:<USERNAME>/<REPO>.git

---

## 10) .gitignore template

# Data folders
data/
outputs/

# Python cache
__pycache__/
*.pyc

# Virtual environments
.venv/
env/
venv/

# Jupyter checkpoints
.ipynb_checkpoints/

# Editor settings
.vscode/

# OS files
.DS_Store
Thumbs.db

---

Tip: Keep this PLAYBOOK.md in your repo root so you never have to Google Git commands again.
