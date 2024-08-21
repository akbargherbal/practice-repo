# Git and GitHub CLI Learning Log

## Authentication Issue and Resolution

### Problem
After installing GitHub CLI and authenticating, the terminal "forgot" the login information when reopened.

### Solution
1. We verified the authentication status using:
   ```
   gh auth status
   ```
2. If not logged in, we reauthenticated using:
   ```
   gh auth login
   ```

### Git User Configuration
We set up Git user information globally:
```
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

## Basic Git and GitHub CLI Commands

1. Create a new repository:
   ```
   gh repo create practice-repo --public
   ```

2. Clone the repository:
   ```
   git clone https://github.com/username/practice-repo.git
   cd practice-repo
   ```

3. Create and add a file:
   ```
   echo "# Practice Repository" > README.md
   git add README.md
   ```

4. Commit changes:
   ```
   git commit -m "Added README file"
   ```

5. Push to GitHub:
   ```
   git push origin main
   ```

6. View repository information:
   ```
   gh repo view
   ```

7. List repositories:
   ```
   gh repo list
   ```

8. Create an issue:
   ```
   gh issue create --title "My first issue" --body "This is a test issue created using GitHub CLI"
   ```

9. List issues:
   ```
   gh issue list
   ```

10. Create a new branch and make changes:
    ```
    git checkout -b feature-branch
    echo "This is a new line" >> README.md
    git add README.md
    git commit -m "Update README.md"
    git push origin feature-branch
    ```

11. Create a pull request:
    ```
    gh pr create --title "Update README" --body "Added a new line to README.md"
    ```

12. List pull requests:
    ```
    gh pr list
    ```