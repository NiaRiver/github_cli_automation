# 📘 GitHub CLI Automation Guide With aliases

This guide will help you install **GitHub CLI**, set up convenient aliases for quickly creating repositories, and use them.

## 🚀 Installing GitHub CLI

### 📌 On Arch Linux (using pacman)
```sh
sudo pacman -S github-cli
```

### 📌 On Debian/Ubuntu (using apt)
```sh
sudo apt update && sudo apt install gh
```

After installation, check the functionality of the command:

```sh
gh --version
```

## 🔑 Authorization in GitHub CLI

Before using **GitHub CLI** you need to log in:

```sh
gh auth login
```
Select **GitHub.com**, then your login method (browser or token).

## ⚡ Configuring Aliases
To simplify repository creation, add the following aliases to your `~/.bashrc` file:

```sh
echo "alias gh-create-readme='git init -b main && echo \"# init repo + README.md\" > README.md && \
git add README.md && git commit -m \"Initial commit\" && \
gh repo create --private --source=. --remote=origin && \
git push -u --all'" >> ~/.bashrc

echo "alias gh-create-main='git init -b main && git add . && git commit -m \"create local branch remote origin and push to remote.\" && \
gh repo create --private --source=. --remote=origin && \
git push -u --all'" >> ~/.bashrc

echo "alias gh-create-remote='git add . && git commit -m \"create remote origin and push to remote.\" && \
gh repo create --private --source=. --remote=origin && \
git push -u --all'" >> ~/.bashrc

source ~/.bashrc
```

## 🛠 Alias Descriptions

| Alias ​​| Description |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `gh-create-readme`  | Initializes the repository with main branch, creates `README.md`, commits and pushes it to GitHub to the new repo with same name as the current directory |
| `gh-create-main`    | Initializes the repository with main branch, adds all files, commits and pushes them to GitHub to the new repo with same name as the current directory |
| `gh-create-remote`  | Creates a remote repository with same name as the current directory and pushes the localy initiated repoitory with all branches to it (without `git init`) |


## 🎯 Usage

Run any of the following commands inside a project directory:

```sh
gh-create-readme  # Initializes a repo with a README and pushes it to GitHub to the new repo with same name as the current directory
gh-create-main    # Initializes a repo with all files and pushes it to GitHub to the new repo with same name as the current directory
gh-create-remote  # Creates a GitHub repo from an existing local repo and pushes to the new repo with same name as the current directory
```

🔥 Now creating and publishing repositories on GitHub is done **in one command**! 🚀
