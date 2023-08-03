## 🌈GIT COMMANDS

### 🔷`git init`

This will create a .git directory in the [project] directory. Make sure that the folder was successfully created (you can run the command ls -l to read the directory content in the command line).

### 🔷`git status` 

It is used to display the current state of the Git repository. It shows information about the files in the working directory and the staging area. It will show:

- Any modified files that have not been staged for commit. (Changes not staged for commit:)
- Any files that are staged and ready to be committed. (Changes to be committed:)
- Any untracked files that are not yet staged, files you have just created. (Untracked files:)
  

### 🔷`git add style.css`  --  `git add "*.txt"`

To have Git to track a file (e.g. style.css) or a type of file (e.g. all .txt files). This process is called Staging, or moving files to the Staging index tree, meaning our changes are ready to be committed


### 🔷`git add .`

It is used to STAGE all changes in the current directory and its subdirectories for the next commit. It adds all modified files and new files to the staging area, preparing them to be included in the next commit. The `.` represents the current directory. If you only want to stage specific files or directories, you can specify their paths instead of using `.`


### 🔷`git commit -m`

The git commit command is used to save the changes made to the files in the repository. It creates a new commit with a unique identifier that represents the changes made. When you run git commit, you need to provide a commit message that describes the changes made in the commit. This message helps others understand the purpose of the commit. The commit message can be added using the -m flag followed by the message in quotes, like this: git commit -m "Commit message here". After running git commit, the changes are permanently saved in the repository's history.

### 🔷`git commit -a -m` 

The -a option tells Git to automatically stage all modified and deleted files before committing. This means that you don't need to explicitly use the `git add` command to stage changes before committing.

### 🔷`git log`

It shows a log of all commits starting from HEAD back to the initial commit. 

### 🔷`git diff` 

It shows the differences between two commits, two branches, or a commit and the working directory. It displays the changes made to the files in a patch format. The output of git diff includes lines that were added, modified, or deleted. By default, git diff compares the working directory with the latest commit. However, you can specify different commits or branches to compare.

### 🔷`git remote add origin https://github.com/vanesascode/project.git`

It associates your local repository with a Github repository you have created.

### 🔷`git push -u origin main`

It pushes the commits from the local branch named "main" to the remote repository named "origin". The -u flag is used to set the upstream branch, meaning that the local branch will be associated with the remote branch for future pushes and pulls.

After running this command, the local commits will be pushed to the "main" branch on the remote repository named "origin". If the "main" branch does not exist on the remote repository, it will be created. If the "main" branch already exists, the commits will be added to it.

This command is typically used for the initial push of a local branch to a remote repository or when setting up tracking of a branch. After the initial push, subsequent pushes can be done using git push without the need for the -u flag.

### 🔷`git push origin main`

To push subsequent commits to your remote repository. 

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

- Switching branches: You can use git checkout <branch-name> to switch to a different branch in your repository. This will update your working directory to reflect the state of the selected branch.

- Creating and switching to a new branch: You can use git checkout -b <new-branch-name> to create a new branch and switch to it in one command.

- Discarding local changes: If you want to discard the changes made to a specific file or the entire working directory, you can use git checkout -- <file> or git checkout -- . respectively. This will restore the file(s) to the state of the last commit.

- Restoring files from a specific commit: You can use git checkout <commit-hash> -- <file> to restore a specific file from a previous commit. This will replace the current version of the file with the version from the specified commit.

Please note that git checkout can be a powerful command that modifies your working directory. It's important to use it with caution, as it can discard or overwrite changes.
