## 🌈GIT CONFIGURATION

🔷 The git config command is used to set configuration options for git. The --global flag indicates that the configuration should be applied globally, meaning it will be used for all git repositories on your machine.

`git config --global user.name "Emma Paris"`
`git config --global user.email "eparis@atlassian.com"`

🔷 The credential.username property is used to store your git username for authentication purposes, such as when interacting with remote repositories that require authentication. After running this command, when git needs to authenticate with a remote repository, it will use your username (e.g. "vanesascode")

`git config --global credential.username "vanesascode"`

🔷 To create your own commands (for example, so you don't have to type 'commit -m' everytime, but just 'cm':

`git config --global.cm "commit -m"`

🔷 To have a folder to put all the stuff you don't want to be pushed to your repo, create a file and call it like this: 

`.gitignore`

🔷 To remove the git main folder from a repository (so every commit and everything is erased, and you have to `git init` again: 

`rm -rf .git`

- rm: This is the command in Unix-like systems used to remove files and directories.
- -rf: These options are passed to the rm command.
- r stands for "recursive" and tells the command to remove directories and their contents.
- f stands for "force" and tells the command to ignore any warnings or prompts and proceed with the removal.
- .git: This is the name of the directory being removed. In a Git repository, the .git directory is the heart of the repository, containing all the version control metadata, such as commit history, branches, tags, and configuration files.

## 🌈GIT COMMANDS

### 🔷`git init`

This will create a .git directory in the [project] directory. Make sure that the folder was successfully created (you can run the command ls -l to read the directory content in the command line).

### 🔷`git status` 

It is used to display the current state of the Git repository. It shows information about the files in the working directory and the staging area. It will show:

- Any modified files that have not been staged for commit. (Changes not staged for commit:)
- Any files that are staged and ready to be committed. (Changes to be committed:)
- Any untracked files that are not yet staged, files you have just created. (Untracked files:)
  

### 🔷`git add style.css`  --  `git add "*.txt"`

To have git to track a file (e.g. style.css) or a type of file (e.g. all .txt files). This process is called Staging, or moving files to the Staging index tree, meaning our changes are ready to be committed

### 🔷`git reset style.css` 

It does the opposite to add. In this case it will remove the style.css file from staging. 

### 🔷`git add .`

It is used to STAGE all changes in the current directory and its subdirectories for the next commit. It adds all modified files and new files to the staging area, preparing them to be included in the next commit. The `.` represents the current directory. If you only want to stage specific files or directories, you can specify their paths instead of using `.`

### 🔷`git reset .`

Takes all files from staging area back into the working area. 

### 🔷`git commit -m ""`

The git commit command is used to save the changes made to the files in the repository. It creates a new commit with a unique identifier that represents the changes made. When you run git commit, you need to provide a commit message that describes the changes made in the commit. This message helps others understand the purpose of the commit. The commit message can be added using the -m flag followed by the message in quotes, like this: git commit -m "Commit message here". After running git commit, the changes are permanently saved in the repository's history.

### 🔷`git commit -a -m ""` 

The -a option tells git to automatically stage all modified and deleted files before committing. This means that you don't need to explicitly use the `git add` command to stage changes before committing.

### 🔷`git commit --amend -m ""` 

Imagine you want to add something to the latest commit, instead of creating a new one. E.g `git commit --amend -m "version 1"` This will overwrite the latest commit, instead of creating a new one. 

### 🔷`git log`

It shows a log of all commits starting from HEAD back to the initial commit (so it dosn't show more moder ones). 

### 🔷`git log --all`

In case you are in commit 2 (for example) and you want to see the commits after that (commit 3, 4, etc) this is the command. (You will see the word HEAD next to the commit you are in at that moment).

### 🔷`git log --all --graph`

It shows you the branching effect in your commit history (you'll see for example, if you went to a previous version and commited it too, in what level it is...) 

### 🔷`git diff` 

It shows the differences between two commits, two branches, or a commit and the working directory. It displays the changes made to the files in a patch format. The output of git diff includes lines that were added, modified, or deleted. By default, git diff compares the working directory with the latest commit. However, you can specify different commits or branches to compare.

### 🔷`git remote add origin https://github.com/vanesascode/project.git`

It associates your local git repository with a git remote repository you have created.

If that didn't work, you can try removing the origin (see below) and adding the link again, but adding your username with @ to the link, like this: 

`git remote add origin https://vanesascode@github.com/vanesascode/project.git`

If that doesn't work either, you can use a Personal Access Token [(see here)](https://www.youtube.com/watch?v=1ibmWyt8hfw)

### 🔷`git remote`

With this command you can see the remote git repository your local git repository is linked to (it will propably show you 'origin', which is how you called it when you linked the two repositories). 

### 🔷`git remote -v`

It gives you all the details of your remote repository, including the URL. 

### 🔷`git remote remove origin`

It unlinks our local git repository with the remote git repository called 'origin' (after that, run `git remote` and you'll see there is no connection!)

### 🔷`git push -u origin main`

It pushes the commits from the local branch named "main" to the remote repository named "origin". The -u flag is used to set the upstream branch, meaning that the local branch will be associated with the remote branch for future pushes and pulls.

After running this command, the local commits will be pushed to the "main" branch on the remote repository named "origin". If the "main" branch does not exist on the remote repository, it will be created. If the "main" branch already exists, the commits will be added to it.

This command is typically used for the initial push of a local branch to a remote repository or when setting up tracking of a branch. After the initial push, subsequent pushes can be done using git push without the need for the -u flag.

### 🔷`git push origin main`

To push subsequent commits to your remote repository. In case it gives you an error(you probably messed up with the branches) and you want to push anyway, then run `git push origin main -f`

### 🔷`git clone https://github.com/vanesascode/git-cheatsheet.git new-git-cheatsheet`

To get the git remote repository into your computer. You add the link of the repository and if you like, you can add a name to the folder (e.g. "new-git-cheatsheet"), otherwise, it would be called like the remote repository(in this case: "git-cheatsheet"). In the terminal, you have to be in the folder you want this new folder to be in. The cloned repository will have a git history and you can keep pushing changes into the original remote repository. 

### 🔷`git fetch`

Imagine you have your remote repository more updated that your local repository, and you want to update your local repository to be like the remote one. This command will fetch the latest changes in the remote repository. Run `git --all --graph` and you will see that you have a commit ahear of your HEAD in your local repository. You'll have to sync this ahead commit into your local repository with the command `git pull origin main`. Run `git --all --graph` to see if it worked. 

### 🔷`git pull origin main`

(see `git fetch`)

***

It is a good practice to always work with the most recent version of your repository, to make sure that you are not ignoring possible important changes by a team member. So, to update your local repository:

### 🔷`git pull`

It is used to fetch and merge changes from a remote repository to your local repository. It is a combination of two actions: `git fetch`, which retrieves the latest changes from the remote repository, and `git merge`, which incorporates those changes into your local branch.

When you run git pull, Git will fetch the latest changes from the remote repository and automatically merge them with your current branch. If there are no conflicts, the changes will be merged seamlessly. However, if there are conflicts between the changes in the remote repository and your local changes, Git will prompt you to resolve the conflicts manually.

It's important to note that git pull will merge the changes from the remote branch into your current branch. If you want to pull changes from a specific remote branch other than the default one, you can specify the branch name as an argument, like this: `git pull origin branch-name`

***
So, once you have pulled the latest version of the remote repository, you may see changes made by another team mate. So, to check them: 

### 🔷`git diff HEAD`

It is used to show the difference between the current state of the working directory and the last commit (HEAD) in the repository.

Running git diff HEAD will display the changes that have been made to the files in the working directory since the last commit. It will show lines that have been added, modified, or deleted.

You can also specify a specific file or directory to see the differences for that specific file or directory. For example, git diff HEAD file.txt will only show the differences for the file.txt file.

To exit the git diff view, you can press q.

***

Now, imagine that, after working for a few minutes updating the content of monthly_meetings.txt, you realize that you made a mistake. Not to worry; we can revert these changes with a Git command.

Type git checkout, followed by the name of the file that you need to revert your changes to.

### 🔷`git checkout` 

It is used to switch between different branches or restore files from a specific commit or branch.

Here are a few common use cases for git checkout:

- Switching branches: You can use git checkout <branch-name> to switch to a different branch in your repository. This will update your working directory to reflect the state of the selected branch (see below) 

- Creating and switching to a new branch: You can use git checkout -b <new-branch-name> to create a new branch and switch to it in one command. (see below) 

- Discarding local changes: If you want to discard the changes made to a specific file or the entire working directory, you can use git checkout -- <file> or git checkout -- . respectively. This will restore the file(s) to the state of the last commit. (see below) 

- Restoring files from a specific commit: You can use git checkout <commit-hash> -- <file> to restore a specific file from a previous commit. This will replace the current version of the file with the version from the specified commit.

Please note that git checkout can be a powerful command that modifies your working directory. It's important to use it with caution, as it can discard or overwrite changes.

### 🔷`git checkout -- .` 

It will remove all the changes you made to your code since the latest commit, so carefull. 

### 🔷`git checkout -- config.js` 

It will remove all the changes you made to the file 'config.js' since the latest commit, so carefull. 

### 🔷`git checkout cc0bd4098113a591acbbff63e6af55b08807e0d9`

It will take you to a specific commit, using its commit 'hash'. However, if you make changes and commit them from here, you'll end up adding a new branch. 

### 🔷`git checkout cc0bd4098113a591acbbff63e6af55b08807e0d9 .`

It will take you to a specific commit, using its commit 'hash', but in this case, if you commit it, this will be the latest commit without creating another branch (always check with `git log --all --graph`) You can also subtitute the dot `.` by a particular file or folder. 

### 🔷`git branch` 

The git branch command is used to list, create, or delete branches in a Git repository.

- When you run git branch without any additional arguments, it will list all the branches in the repository. The current branch will be indicated with an asterisk (*).

- To create a new branch, you can use git branch <branch-name>. This will create a new branch with the specified name based on the current commit or the commit that the current branch is pointing to.

- To delete a branch, you can use git branch -d <branch-name>. This will delete the specified branch. However, you cannot delete the branch you are currently on. If you want to delete a branch forcefully, you can use git branch -D <branch-name>.

- Additionally, you can use the git branch -m <new-branch-name> command to rename the current branch to a new name.

***
***

Once you create a new branch, you have to switch to it to be able to work with it. So, for example, after the creation with `git branch my_version`, run:

`git checkout my_version`

After committing your changes to your new branch, you should merge it with the main branch, so that the rest of our team all have the same project structure. Let's switch to the main branch first:

`git checkout main`

You will see that the main branch has not been altered, so the changes you did in your own branch are not reflected to the main's branch folder structure. Let's apply our changes to the master branch. So, to merge your branch my_version with the main branch run:  

### 🔷`git merge my_version`

The git merge command affects the branch you are currently on. It integrates the changes from the specified source branch into the current branch.

***

So, if you're not going to be using your my_version branch anymore, let's delete it. It is a good practice to delete unused branches, as, as our project increases, having many branches can be hard to maintain and many of the older branches can be left behind in updates:

`git branch -d my_version`

So, now, the last thing is to share the repository with our team so that we can all work in it. Let's upload our repository to GitHub.

`git push`
