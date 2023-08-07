# GIT CHEATSHEET

Notes to remember how to work with Git and Github. It includes: 

1. Configuration setup
2. General commands
   - Commands to push to remote from local
   - Commands to pull to local from remote
3. Branching and merging
   - Merge conflicts
4. The Feature Branch Workflow

## 1. GIT CONFIGURATION

🔷 The git config command is used to set configuration options for git. The --global flag indicates that the configuration should be applied globally, meaning it will be used for all git repositories on your machine.

`git config --global user.name "Emma Paris"`

`git config --global user.email "eparis@atlassian.com"`

***

🔷 The credential.username property is used to store your git username for authentication purposes, such as when interacting with remote repositories that require authentication. After running this command, when git needs to authenticate with a remote repository, it will use your username (e.g. "vanesascode")

`git config --global credential.username "vanesascode"`

***

🔷 To create your own commands (for example, so you don't have to type 'commit -m' everytime, but just 'cm':

`git config --global.cm "commit -m"`

***

🔷 To have a folder to put all the stuff you don't want to be pushed to your repo, create a file and call it like this: 

`.gitignore`

***

🔷 To remove the git main folder from a repository (so every commit and everything is erased, and you have to `git init` again: 

`rm -rf .git`

- rm: This is the command in Unix-like systems used to remove files and directories.
- -rf: These options are passed to the rm command.
- r stands for "recursive" and tells the command to remove directories and their contents.
- f stands for "force" and tells the command to ignore any warnings or prompts and proceed with the removal.
- .git: This is the name of the directory being removed. In a Git repository, the .git directory is the heart of the repository, containing all the version control metadata, such as commit history, branches, tags, and configuration files.

🔷 HEAD = points to the branch we are currently working on.


***
***

## 2. GENERAL COMMANDS

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

### 🔷`git checkout -- .` 

It will remove all the changes you made to your code since the latest commit, so carefull. 

### 🔷`git checkout -- config.js` 

It will remove all the changes you made to the file 'config.js' since the latest commit, so carefull. 

### 🔷`git checkout cc0bd4098113a591acbbff63e6af55b08807e0d9`

It will take you to a specific commit, using its commit 'hash'. However, if you make changes and commit them from here, you'll end up adding a new branch. 

### 🔷`git checkout cc0bd4098113a591acbbff63e6af55b08807e0d9 .`

It will take you to a specific commit, using its commit 'hash', but in this case, if you commit it, this will be the latest commit without creating another branch (always check with `git log --all --graph`) You can also subtitute the dot `.` by a particular file or folder.

### 🔷`git log`

It shows a log of all commits starting from HEAD back to the initial commit (so it dosn't show more moder ones). 

### 🔷`git log --all`

In case you are in commit 2 (for example) and you want to see the commits after that (commit 3, 4, etc) this is the command. (You will see the word HEAD next to the commit you are in at that moment).

### 🔷`git log --all --graph`

It shows you the branching effect in your commit history (you'll see for example, if you went to a previous version and commited it too, in what level it is...) 

### 🔷`git diff` 

It shows the differences between two commits, two branches, or a commit and the working directory. It displays the changes made to the files in a patch format. The output of git diff includes lines that were added, modified, or deleted. By default, git diff compares the working directory with the latest commit. However, you can specify different commits or branches to compare.

### 🔷`git diff HEAD`

It is used to show the difference between the current state of the working directory and the last commit (HEAD) in the repository.

Running git diff HEAD will display the changes that have been made to the files in the working directory since the last commit. It will show lines that have been added, modified, or deleted.

You can also specify a specific file or directory to see the differences for that specific file or directory. For example, git diff HEAD file.txt will only show the differences for the file.txt file.

To exit the git diff view, you can press `q`

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

### 🟡 From local to remote: 

### 🔷`git push -u origin main`

It pushes the commits from the local branch named "main" to the remote repository named "origin". The -u flag is used to set the upstream branch, meaning that the local branch will be associated with the remote branch for future pushes and pulls.

After running this command, the local commits will be pushed to the "main" branch on the remote repository named "origin". If the "main" branch does not exist on the remote repository, it will be created. If the "main" branch already exists, the commits will be added to it.

This command is typically used for the initial push of a local branch to a remote repository or when setting up tracking of a branch. After the initial push, subsequent pushes can be done using git push without the need for the -u flag.

### 🔷`git push origin main`

To push subsequent commits to your remote repository. In case it gives you an error(you probably messed up with the branches) and you want to push anyway, then run `git push origin main -f`

### 🟡 From remote to local: 

### 🔷`git clone https://github.com/vanesascode/git-cheatsheet.git new-git-cheatsheet`

To get the git remote repository into your computer. You add the link of the repository and if you like, you can add a name to the folder (e.g. "new-git-cheatsheet"), otherwise, it would be called like the remote repository(in this case: "git-cheatsheet"). In the terminal, you have to be in the folder you want this new folder to be in. The cloned repository will have a git history and you can keep pushing changes into the original remote repository. 

### 🔷`git pull`

It is a good practice to always work with the most recent version of your repository, to make sure that you are not ignoring possible important changes by a team member. So, to update your local repository you use this command. 

It is used to fetch and merge changes from a remote repository to your local repository. It is a combination of two actions: `git fetch`, which retrieves the latest changes from the remote repository, and `git merge`, which incorporates those changes into your local branch.

When you run git pull, Git will fetch the latest changes from the remote repository and automatically merge them with your current branch. If there are no conflicts, the changes will be merged seamlessly. However, if there are conflicts between the changes in the remote repository and your local changes, Git will prompt you to resolve the conflicts manually.


### 🔷`git fetch`

Imagine you have your remote repository more updated that your local repository, and you want to update your local repository to be like the remote one. This command will fetch the latest changes in the remote repository. Run `git --all --graph` and you will see that you have a commit ahead of your HEAD in your local repository. You'll have to sync this ahead commit into your local repository with the command `git pull origin main`. Run `git --all --graph` to see if it worked. 

### 🔷`git pull origin main`

(see `git fetch`)


## 3. Branching and Merging: 


### 🔷`git branch` 

It will list all the branches in the repository. The current branch will be indicated with an asterisk (*). 

### 🔷`git branch <branch-name>`

This will create a new branch with the specified name based on the current commit or the commit that the current branch is pointing to.

### 🔷`git branch -d <branch-name>`

This will delete the specified branch. However, you cannot delete the branch you are currently on. If you want to delete a branch forcefully, you can use `git branch -D <branch-name>`

It is a good practice to delete unused branches. As our project increases, having many branches can be hard to maintain and many of the older branches can be left behind in updates.

### 🔷`git branch -m <new-branch-name>` 

It is used to rename the current branch to a new name.

### 🔷`git checkout <branch-name>`

It is used to switch to a different branch in your repository. This will update your working directory to reflect the state of the selected branch. 

👉 Once you create a new branch, you have to switch to it to be able to work with it. Do it with this command. 

### 🔷`git checkout -b <new-branch-name>` 

To create a new branch and switch to it in one command. 

### 🔷`git checkout main`

After committing your changes to your new branch, you may want to merge it with the main branch, so that the rest of our team all have the same project structure. You have to switch to the main branch with this command. You will see that the main branch has not been altered, so the changes you did in your own branch are not reflected to the main's branch folder structure. To apply your changes to the main branch you have to merge your <branch-name> with the main branch using the following command:   

### 🔷`git merge <branch-name> -m ""`

The git merge command affects the branch you are currently on. It integrates the changes from the specified source branch into the current branch. So, imagine you are in the main branch right now, and you want to merge the changes of another branch. You run this command then, and add a name to the commit with the -m flag. 

Something you'll want to do at this moment is to upload the merged project into the remote repository. Remember to run `git push` then. 

![branching-example](https://github.com/vanesascode/git-cheatsheet/assets/131259155/95d9814c-5aa5-416d-b984-2b1cbe9e143d)

Pic from [SuperSimpleDev](https://www.youtube.com/watch?v=Q1kHG842HoI&t=35s)

### 🟡 Merge Conflicts: 

A merge conflict in Git occurs when there are conflicting changes made to the same part of a file or multiple files that are being merged. This typically happens when two different branches have made conflicting modifications to the same lines of code. Git is unable to automatically determine which changes should be preserved, so it marks the conflicting sections and asks the user to manually resolve the conflict. Resolving a merge conflict involves reviewing the conflicting changes, deciding which changes to keep, and making the necessary adjustments to the code.

![merge-conflict-1](https://github.com/vanesascode/git-cheatsheet/assets/131259155/6b4b648b-152d-46c4-8018-2d44dc286236)

Pic from [SuperSimpleDev](https://www.youtube.com/watch?v=Q1kHG842HoI&t=35s)

In your coding you'll have to choose the lines you want to keep. You have to erase the ones you don't want. Basically you have to tell git what is the final code. 

And then, you'll have to make a new commit. Remember to `git log --all --graph` all the time to keep seeing what's going on. 

## 3. Feature Branch Workflow: 

The feature branch workflow is a Git branching strategy where each new feature or task is developed in a separate branch. Here's a simplified summary of the steps involved: 
 
1. Create a new branch for the feature/task. 
2. Work on implementing the feature/task in this branch. 
3. Regularly commit changes to track progress. 
4. Keep the branch up to date with the latest changes from the main branch. 
5. Test and review the feature/task. 
6. Merge the feature branch back into the main branch. 
 
This workflow allows for independent development, easy collaboration, and helps maintain a clean main branch.

***

#### EXAMPLE: 

👉 You have been working on a new feature using the main branch of a local repository. What's next: 

◻ `git branch new-feature`

◻ `git log --all --graph` 

◻ `git checkout new-feature`

◻ `git log --all --graph`

◻ `git add .`

◻ `git commit -m "new feature"`

◻ `git log --all --graph`

👉 You want to upload both versions into a remote repository. You create a Github repository. What's next:

◻ `git remote add origin <url>`

◻ `git checkout main` (or master, check with `git log --all --graph`)

◻ `git push origin main` 

◻ Check in the github webpage that it's correctly uploaded. 

◻ `git checkout new-feature`

◻ `git push origin new-feature` 

◻ Check in the github remote repository it's all correct and you have the 2 branches.  

👉 You want your team to review your branch before merging it with the main branch. What's next: 

◻ Check in the github remote repository. It probably gives you a message button you have to click: 'Compare and pull request' or you have to create a pull request yourself (then, choose the main and the branch to be compared) Write a good description.

◻ Copy the url of this pull request and send it to your team to be reviewed. There, in the different tabs, there's all the information about the commits, the code itself, etc.

◻ If they don't like your code, they'll probably send you a message you will see in the conversation tab. If they liked it and want to merge it, they will do it with the button 'Merge pull request' in the same pull request webpage. You'll receive a notification. 

👉 You want to update the local repository after the merge. What's next:

◻ `git fetch`

◻ `git log --all --graph` (see that above your HEAD, there's the merge that took place in the remote repository)

◻ `git checkout main`

◻ `git pull origin main`

◻ `git log --all --graph` (see that our HEAD is at the same level as the origin remote repository) 

◻ `git branch -D new-feature` (if you don't need that branch anymore) 

👉 The reviewer wants to solve a merge conflict when you are working with other collegues that are merging their branches in the main branch too: 

![merge-conflict-2](https://github.com/vanesascode/git-cheatsheet/assets/131259155/38bd72ab-8cff-427e-8ccf-f037c0d592c3)

Pic from [SuperSimpleDev](https://www.youtube.com/watch?v=Q1kHG842HoI&t=35s)

The reviewer will find the conflict when, after merging a pull request, wants to merge another pull request but Github tells them: "this branch has conflicts that must be resolved". Below that, the reviewer can open the "web editor" and erase everything except from what they want the final code to keep. 




