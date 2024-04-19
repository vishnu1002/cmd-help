![git-logo](https://github.com/vishnu1002/cmd-help/assets/145321614/5832a508-964f-492f-8baf-d5d6b84555f2)


Git is a distributed version control system, which means it assists in tracking changes made to files over time, usually source code. In order to oversee the progress of the Linux kernel, Linus Torvalds founded it in 2005. Git keeps track of the changes made by each contributor while enabling numerous developers to work together on a project at once. Learn more 
[git-scm.com/about](https://git-scm.com/about)
 
GitHub, on the other hand, is a web-based repository hosting platform for Git files. Developers can work together on projects and save their Git repositories in the cloud using this platform. With features like pull requests, code review tools, issue tracking, and project management capabilities, GitHub is a well-liked option for both private and open-source software development projects. 
Learn more [github.com/about](https://github.com/about)

## Setup Git
Follow the link to Install Git for respective OS:
- [Install for Linux](https://git-scm.com/download/linux)
- [Install for macOS](https://git-scm.com/download/mac)
- [Install for Windows](https://git-scm.com/download/win)

## Setup GitHub
- Sign in/Sign up
- Create a demo repository

[Setup Git](#setup)
[Initialize](#initialize)
[Staging](#staging)
[Branch and Merge](#branch-and-merge)
[Path Changes](#path-changes)
[Share and Update](#share-and-update)
[Generate Token](#generate-token)

## Git Commands --list

### Setup
Configure user information used accross all system/global/local repositories:

    git config --global user.name "<github-username>"
    git config --global user.email "<github-email>"
	git config --global color.ui auto

Verify config:

    git config -l

### Initialize
Existing directory as a Git repository:

    git init

or, clone entire repo:

    git clone <url.git>

### Staging 
Display the status of the repo:

    git status

Add files to the staging area:

    git add <file-name>
    git add .

Unstage file:

    git reset <file-name>

Commit changed:

    git commit -m "<message>"

### Branch and Merge
List available branches:

    git branch

Create a new branch:

    git branch <branch-name>

Merge given branch with current one:

    git merge <branch-name>

Display all commits and branch history:

    git log

### Path Changes
Delete a file from project:

    git rm <file-name>

Change file location:

    git mv <existing-path> <new-path>

### Share and Update
Add remote URL:

    git remote add <alias> <url>

Set remote URL with generated token:

    git remote set-url origin https://<username>:<token>@github.com/<username>/<repository>.git

Push the updated files to remote repo:

### Generate Token

    git push <alias> <branch-name>

Pull updated files from remote repo:

    git pull

