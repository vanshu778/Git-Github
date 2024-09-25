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
