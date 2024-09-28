# Git and GitHub Tutorial

## What is Git?

**Git** is a version control system that helps track changes to files and enables collaboration with others. It manages the history of your code and allows you to merge changes from different branches.

If terms like version control, branches, and merges are new to you, don't worry! We'll cover these concepts in this tutorial.

---

## Difference Between Git and GitHub

- **Git**: A software-based version control system, free and open source, available for Windows, macOS, and Linux. It helps you track and manage changes to your files locally.
- **GitHub**: A web-based platform where you can host Git repositories. It allows developers to collaborate, share code, and use Git in the cloud. Alternatives like **GitLab** and **Bitbucket** exist.

---

## Version Control Systems (VCS)

A **Version Control System (VCS)** is crucial in software development for managing the history of your code. It allows you to:
- Track changes to files
- Create checkpoints (versions) to which you can return if needed
- Collaborate with other developers without losing progress

### Why Use a VCS?
Think of it like a video game checkpoint—you can always return to a previous point if something goes wrong.

---

## Evolution of Version Control Systems

Before Git, developers used systems like **SCCS (Source Code Control System)**, which was proprietary and not user-friendly. Git was created as a more accessible, open-source solution. Other VCS tools include:
- **Subversion (SVN)**
- **CVS**
- **Perforce**

---

## Learning Path for Git and GitHub

To master Git and GitHub, follow these steps:
1. **Get the basics**
2. **Use it daily**
3. **Face problems**
4. **Solve them**
5. **Learn more**

We'll focus on Git first, then move to GitHub for easier collaboration and hosting.

---

## Installing Git

Git is available for:
- **Windows**
- **macOS**
- **Linux**

You can install Git by downloading it from the [official Git website](https://git-scm.com/), or via the command line depending on your operating system.

---

## Setting Up GitHub Account

To start using GitHub:
1. Create an account on [GitHub](https://github.com/).
2. Link GitHub to your local machine through **SSH key setup** for enhanced security. (Password authentication is no longer recommended for pushing code to GitHub.)

---

## Git Concepts in Simple Terms

### Checkpoints (Version Control)
Git allows you to create **checkpoints** in your software development process. If something goes wrong, you can roll back to an earlier point, a core feature of version control.

### Git Flexibility
With Git, you can:
- Jump between different points in your code (checkpoints)
- Make changes and either commit or discard them as required

---

## Conclusion

Git and GitHub are essential tools for modern software development. Start by understanding the basics of Git, practice daily, troubleshoot issues, and gradually enhance your knowledge of GitHub for better collaboration and project hosting.

---

### Further Reading

- [Git Documentation](https://git-scm.com/doc)
- [GitHub Documentation](https://docs.github.com/en)

# Git and GitHub Terminology

#### Checking Your Git Version
To find out what version of Git is installed on your system, run the following command in your terminal:

```bash
git --version
```

This will display your installed Git version. From my experience, Git is quite stable and usually avoids breaking changes.

#### What is a Repository?
A **repository** is a collection of files and directories stored together, allowing you to manage your code effectively. While it resembles a regular folder on your computer, it offers more functionality—it can hold files, folders, and even other repositories. Think of a repository as a container for all your code.

It's important to note that tracking a repository with Git differs from just having software on your system. You can check the current state of your repository at any time by running:

```bash
git status
```

#### Understanding Your Config Settings
GitHub provides a plethora of settings you can customize, such as your username and email. When you make a commit, Git records this information. All your configurations are stored in a `.gitconfig` file. You can set global options as well as repository-specific settings.

Let’s configure your email and username. I recommend creating a GitHub account first and using that email and username:

```bash
git config --global user.email "your-email@example.com"
git config --global user.name "Your Name"
```

You can verify your configuration settings with:

```bash
git config --list
```

This command will display all the settings you've modified.

---

### Creating a Repository
Creating a repository involves initializing a new folder on your system to track with Git. It’s simply a regular folder for your project, but by using Git, you're asking it to keep track of changes. Use the following commands:

```bash
git init
git status
```

The `git init` command initializes a new repository by adding a hidden `.git` folder to your project.

#### Understanding Commits
A **commit** is your way of saving changes to your repository. It acts as a snapshot of your code at a specific time. When you commit, you instruct Git to permanently store your changes, allowing you to revisit that state later.

Here's how the usual flow works:

1. Initialize a new repository with `git init`.
2. Stage your files with `git add`.
3. Commit your changes with `git commit`.
4. Push your commits to GitHub using `git push`.

#### Staging Files
To stage files for tracking, use:

```bash
git add <file1> <file2>
git status
```

This command stages your files, indicating that they are ready to be committed.

#### Committing Changes
To commit your staged changes, use:

```bash
git commit -m "Your commit message"
git status
```

The `-m` flag allows you to include a brief message describing your changes. If you omit the `-m` flag, your default editor (often VIM) will open for you to enter a message. We'll change this to VSCode in a later section.

#### Viewing Commit Logs
To see the history of your commits, run:

```bash
git log
```

This command displays all commits made to the repository. You can simplify the output with the `--oneline` flag to view just the commit messages.

☕️ - Check the Git log documentation for more details.

Using **atomic commits** ensures that each commit is a self-contained unit of work. This way, if one commit encounters an issue, you can revert to a previous commit without complications, helping to maintain a clear and organized project history.

---

### Changing Your Default Code Editor
If you'd like to set VSCode as your default code editor, run:

```bash
git config --global core.editor "code --wait"
```

---

### Using .gitignore
The **.gitignore** file specifies which files and folders Git should ignore, preventing them from being tracked. Create a `.gitignore` file and list the files or folders you want to exclude, for example:

```
node_modules
.env
.vscode
```

Now, running `git status` won't show these ignored folders as being tracked.

---

### Conclusion
In this section, we've covered the basics of Git and how to use it for tracking changes in your files and folders. You’ve also learned about essential commands like `init`, `add`, `commit`, and `log`. By the end of this guide, you should feel confident in using Git effectively to manage your code.

# Git Behind-the-Scenes

A detailed guide to understanding how Git stores and manages snapshots of your code, along with the essential objects that Git uses behind the scenes. This repository explores the fundamental building blocks of Git: Commit Object, Tree Object, and Blob Object.

## Snapshots in Git

Git represents your code at a specific point in time through snapshots. These snapshots are stored locally in a key-value database and are uniquely identified by a hash.

### 3 Key Objects of Git (The Three Musketeers)

1. **Commit Object**  
   The Commit Object contains:
   - A reference to the Tree Object.
   - A reference to the Parent Commit Object (if applicable).
   - Author and committer details.
   - Commit message.

2. **Tree Object**  
   The Tree Object acts as a container for files and folders at the time of the commit. It stores:
   - File mode (permissions).
   - File name.
   - File hash (reference to the Blob Object).
   - Parent tree (for subdirectories).

3. **Blob Object**  
   The Blob Object stores the actual content of files as a key-value pair:
   - Key: File name.
   - Value: File content.

## Git Commands to Explore Internals

Explore the internals of Git by using the following commands:

- **View Commit Object**  
  Displays detailed information about a specific commit.
  ```bash
  git show -s --pretty=raw <commit-hash>

- **View Tree Object**  
  Lists the files and folders tracked by a specific tree object.
  ```bash
  git ls-tree <tree-id>

- **View Blob Object**  
  Displays the actual contents of a file stored in the blob object.
  ```bash
  git show <blob-id>

- **View Commit Details**  
  Displays detailed information about a commit, including the associated tree and parent commit.
  ```bash
  git cat-file -p <commit-id>

## Conclusion
Understanding Git's internals is crucial for anyone looking to master version control. By exploring Git's three key objects — Commit, Tree, and Blob — you can gain a deeper understanding of how Git manages and stores your project at various points in time. This knowledge empowers developers to make more informed decisions when working with version control systems, allowing them to troubleshoot, optimize, and contribute more effectively to projects.

We hope this guide serves as a valuable resource in your journey to becoming proficient with Git.

# Git Branching and Merging

## Overview
Git branches allow developers to work on different versions of a project simultaneously. This functionality is essential for:
- Feature development
- Bug fixes
- Experiments

By using branches, you can make changes without affecting the `main` branch until the changes are merged.
<p align="center">
<img width="342" alt="Branch" src="https://github.com/user-attachments/assets/61e5864f-5262-46a0-8f94-1afdb01a0681">
</p>

---

## Branch Structure

- **Main Branch**: The central line of development (formerly known as `master`).
- **Feature Branches**: Created from the main branch to work independently. Examples include `bug-fix`, `dark-mode`, etc.

---

## Git HEAD
`HEAD` is a pointer that references the current branch and its latest commit.

---

## Branch Management Commands

1. **List Branches**:
   ```bash
   git branch
   
2. **Create a New Branch**:
   ```bash
   git branch <branch-name>

3. **Switch to a Branch**:
   ```bash
   git switch <branch-name>

4. **Create and Switch to a New Branch**:
   ```bash
   git switch -c <branch-name>

5. **Checkout an Existing Branch**:
   ```bash
   git checkout <branch-name>

6. **View Commit History**:
   ```bash
   git log

## Merging Branches

### Fast-Forward Merge
Occurs when the branch being merged has no diverging commits.
<p align="center">
<img width="365" alt="Fast-Forward" src="https://github.com/user-attachments/assets/4a9ff81c-d764-4a0e-a080-d7927c190c06">
</p>

1. **Switch to the `main` branch**:
   ```bash
   git checkout main

2. **Merge the bug-fix branch**:
   ```bash
   git merge bug-fix

### Not Fast-Forward Merge
Occurs when both branches have diverged, which requires conflict resolution.
<p align="center">
<img width="367" alt="Not Fast-Forward" src="https://github.com/user-attachments/assets/6806b49c-b3f9-4d88-a2c0-10ca553cbd48">
</p>

1. **Merge the bug-fix branch**:
   ```bash
   git merge bug-fix

### Conflict Resolution
Conflicts arise when changes in both branches modify the same lines of code.
<p align="center">
  <img width="487" alt="Conflict Resolution" src="https://github.com/user-attachments/assets/3dedf843-aa08-4d53-ac43-5f6c1dd875e9">
</p>

1. **Check Status**:
   ```bash
   git status

2. **Resolve Conflicts**:
Open the conflicted file (e.g., file2.txt) in your code editor and manually resolve conflicts.

3. **After Resolving**:
   ```bash
   git add <file>
   git commit -m "resolved conflicts"

### Managing Conflicts
- There is no automatic solution for conflicts.
- They must be manually resolved using tools like VSCode or GitHub's built-in merge tool.

### Additional Commands

1. **Rename a Branch**:
   ```bash
   git branch -m <old-branch-name> <new-branch-name>

2. **Delete a Branch**:
   ```bash
   git branch -d <branch-name>

3. **Checkout a Branch**:
   ```bash
   git checkout <branch-name>

### Conclusion
Understanding branching and merging in Git is crucial for effective collaboration in development projects. By mastering these concepts, you'll enhance your ability to manage code changes, resolve conflicts, and work efficiently with your team.

# Diff stash and Tags

## Git Diff

The `git diff` command shows the differences between two commits or changes made in different areas of your repository. Git treats different versions of the same file as two separate files and shows differences between them.

### How to Read the Diff
- `a/`: Indicates File A.
- `b/`: Indicates File B.
- `---`: Start of File A.
- `+++`: Start of File B.
- `@@`: Line number of changes.

### Comparing Changes
1. **Working Directory vs. Staging Area**:
   ```bash
   git diff
- Shows unstaged changes.

2. **Staging Area vs Repository**:
   ```bash
   git diff --staged
- Displays changes staged for the next commit.

3. **Comparing Branches**:
   ```bash
   git diff <branch-one> <branch-two>
   
- Alternative:
   ```bash
   git diff branch-one..branch-two

4. **Comparing Specific Commits**:
   ```bash
   git diff <commit-hash-one> <commit-hash-two>

### Git Stash

   The git stash command is used to temporarily save your work without committing it, useful when you need to switch branches.
   
1. **Save Changes**:
   ```bash
   git stash

2. **Name the Stash**:
   ```bash
   git stash save "work in progress on X feature"

3. **View Stash List**:
   ```bash
   git stash list

4. **Apply Stash**:
   ```bash
   git stash apply

5. **Apply Specific Stash**:
   ```bash
   git stash apply stash@{0}

6. **Apply and Drop Stash**:
   ```bash
   git stash pop

7. **Drop Stash**:
   ```bash
   git stash drop

8. **Clear Stash**:
   ```bash
   git stash clear

### Git Tags

   Tags in Git are used to mark specific points in your repository, such as for releases or significant changes.
   
1. **Create a Tag**:
   ```bash
   git tag <tag-name>

2. **Create an Annotated Tag**:
   ```bash
   git tag -a <tag-name> -m "Release 1.0"

3. **List All Tags**:
   ```bash
   git tag

4. **Tag a Specific Commit**:
   ```bash
   git tag <tag-name> <commit-hash>

5. **Push Tags to Remote**:
   ```bash
   git push origin <tag-name>

6. **Delete a Tag**:
   ```bash
   git tag -d <tag-name>

7. **Delete Tag on Remote**:
   ```bash
   git push origin :<tag-name>

### Git Reflog

   The git reflog command tracks updates to the HEAD reference and allows you to see your project's history, including changes and checkouts.
   
1. **View Reflog**:
   ```bash
   git reflog

### Resetting to a Specific Commit

   To reset your branch to a specific commit:
   
1. **Reset**:
   ```bash
   git reset --hard <commit-hash>
   
### Conclusion

   This README covers essential Git commands related to git diff, git stash, git tag, and git reflog. Mastering these commands will allow you to manage your repository more effectively.
