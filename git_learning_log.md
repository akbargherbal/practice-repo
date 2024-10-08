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

## Platform-Specific Commands

### Creating Files

1. On Unix-like systems (Linux, macOS):

   ```
   touch filename.txt
   ```

2. On Windows:
   ```
   echo. > filename.txt
   ```
   Note: This creates an empty file. To add content directly from the command line:
   ```
   echo Some content > filename.txt
   ```

Remember to use platform-appropriate commands when following Git tutorials or guides.

## Understanding Git Branches

### Analogy 1: The Book Writing Process

Imagine you're writing a book. The main story is your 'main' branch. Now, you want to experiment with a different plot twist:

- You don't want to change your original story just yet, so you make a photocopy of your manuscript. This is like creating a new branch.
- You write your new idea on this copy. This is like committing changes to your new branch.
- If you like the new plot twist, you can incorporate it back into your original manuscript. This is like merging the branch.
- If you don't like it, you can simply discard the photocopy. No harm done to your original story!

### Analogy 2: The Parallel Universes

Think of your project as a timeline, and branches as parallel universes:

- The main branch is the primary timeline.
- When you create a new branch, you're creating a parallel universe that's identical to the main timeline up to that point.
- In this new universe (branch), you can make changes without affecting the main timeline.
- If the changes in the parallel universe work well, you can merge them back into the main timeline.
- If they don't work out, you can simply stop working on that universe (branch) without affecting the main timeline.

### Analogy 3: The Road Trip

Imagine you're on a road trip:

- The main road you're traveling on is your 'main' branch.
- You see a interesting side road and decide to explore it. This is like creating a new branch.
- You drive down this side road, making stops (commits) along the way.
- If you find something great, you can rejoin the main road (merge your branch).
- If the side road doesn't lead anywhere interesting, you can simply turn back and return to the main road, as if you never left.

### In Practice

In Git, you can create a new branch with:

```
git branch new-feature
```

Switch to the new branch:

```
git checkout new-feature
```

Or create and switch in one command:

```
git checkout -b new-feature
```

Make changes, commit them, and when ready, merge back to main:

```
git checkout main
git merge new-feature
```

Branches allow you to experiment, develop features, or fix bugs in isolation, without risking the stability of your main codebase. They're a fundamental feature that makes Git powerful for collaboration and managing complex projects.

## Understanding 'master' vs 'main' Branch Names

### Historical Context

- Traditionally, the default branch in Git was called 'master'.
- You would often see commands like:
  ```
  git push origin master
  ```

### The Change to 'main'

- In 2020, GitHub (and subsequently other platforms) began changing the default branch name from 'master' to 'main'.
- This change was part of an industry-wide effort to use more inclusive language in tech.

### Are 'master' and 'main' the same?

- Functionally, 'master' and 'main' are the same – they both refer to the default or primary branch of a repository.
- The difference is purely in the naming convention.

### Current Status

- New repositories created on GitHub now use 'main' as the default branch name.
- Existing repositories may still use 'master' unless manually changed.
- You might see either:
  ```
  git push origin main
  ```
  or
  ```
  git push origin master
  ```
  depending on when the repository was created or if it has been updated.

### Best Practice

- For new projects, it's recommended to use 'main' as the default branch name.
- When working on existing projects, check which name is being used (you can see this on the GitHub repository page or by running `git branch` locally).

### How to Check Your Default Branch Name

You can check the name of your current branch with:

```
git branch --show-current
```

### Changing from 'master' to 'main'

If you want to rename your default branch from 'master' to 'main', you can use these steps:

1. Rename the branch locally:
   ```
   git branch -m master main
   ```
2. Push the new branch and set the remote to track it:
   ```
   git push -u origin main
   ```
3. Change the default branch on GitHub (in repository settings)
4. Delete the old 'master' branch on the remote:
   ```
   git push origin --delete master
   ```

Remember, when collaborating, it's important to communicate such changes with your team to avoid confusion.

## Start and Finish Branches in Programming Tutorials

In many programming tutorials or courses, instructors use Git branches to provide snapshots of the project at different stages. This is particularly useful for complex projects or courses that build on previous work.

### Purpose of Start and Finish Branches

1. Start Branch:

   - Represents the starting point for a particular lesson or section.
   - Contains all the necessary setup and code from previous lessons.
   - Allows students to begin the lesson with the correct baseline, even if they skipped previous sections.

2. Finish Branch:
   - Represents the end state of the project after completing the lesson.
   - Contains all the changes and additions made during the lesson.
   - Useful for students to compare their work or to continue from if they had difficulties.

### Benefits

- Flexibility: Students can jump into any part of the course without needing to complete all previous sections.
- Reference: Provides a clear reference for the expected state of the project at each stage.
- Troubleshooting: Students can compare their work with the finish branch to identify issues.

### How to Use Start and Finish Branches

1. To start a lesson:

   ```
   git checkout lesson-5-start
   ```

2. To see the completed lesson:

   ```
   git checkout lesson-5-finish
   ```

3. To compare your work with the finished version:
   ```
   git diff lesson-5-finish
   ```

### Example Scenario

In a Django course that requires CSS knowledge:

1. The instructor provides a `add-styling-start` branch with basic HTML structure.
2. Students who know CSS can work on this branch to add styles.
3. Students who want to skip the CSS part can checkout the `add-styling-finish` branch, which includes the completed CSS.
4. The next lesson (e.g., Django views) starts from the `add-styling-finish` state, ensuring all students begin with the same styled template.

This approach allows the course to cover CSS for those interested while providing a way for others to skip directly to Django-specific content.
