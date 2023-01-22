# GiTutorial - Practical Tutorial for Git
### Table of Contents
 - [Branching](#branching)
 - [Staging](#staging)
 - [Committing](#committing)
 - [Publishing](#publishing)
 - [Pulling](#pulling)
 - [Further Reading](#further-reading)
<br />

Hi! This repository is an extremely rudimentary introduction to help novices, such as myself, learn and become familiarized with git. 
It's purpose is meant to be more practical than informational, so one can learn more through use/application rather than instruction.

To start, the files included in this tutorial are meant to help practice the given commands shown below, but are in no way necessary. They're empty anyhow.

This tutorial assumes proficiency with linux commandline, only insofar of the utilization of command 'cd' and basic knowledge of text editing using nano/emac/vim/specific respective text editor.

Please note git has kind of three "stages" to progressing and recording your changes: Staging, where you essentially denote changes have been made to files on the local machine for record keeping. Committing, where changes are sent to the repository for other collaborators to see. Finally online repository pushing, where changes to the local repository are published to an online host, public for anyone on the internet to see (granted the repository isnt made private of course). Recall git files are stored on the respective filesystem directory, so wherever the files are, repository and change information is contained.
<br />

## Beginning
If you wish to begin with already published/public files, begin by running in commandline
```
git clone <repository url>
```
This will download the repository to one eponymous file in the current directory you find yourself in, and have 
it initialized to be modified by git.

If not, then after the creation or localization of the respective folder you wish to initialize into git, do so using
```
git init
```
while inside the folder. 
<br />

## **Branching**
After the creation of a local repository, you will find yourself in the 'master' or 'main' branch of the project, 
which is analogous to an official directory. When working, its best not to modify the official directory 
until changes can be verified/tested, so we "branch off" with a clone of the main directory for whatever purposes 
needed.

To branch, while in the current repository directory, run
```
git branch <new branch name>
```
to create a new branch.

To move between branches, run
```
git checkout <branch name>
```

To list all branches, run
```
git branch -a
```
where green branches are modified, and red branches are remote branches. To delete a branch, checkout out of the branch, and run
```
git branch -d <branch name>
```

should you have cloned a repository which has its own remote branches, and you want a local branch to update with remote branch contents and changes run
```
git fetch origin <remote branch>
```
to pull updates from the remote branch, then
```
git branch -u <name of a new local branch> origin/<name of remote branch>
```
> **Note** Default branch is the 'master' or 'main' branch. Any modifications you create will modify the root repository, so be sure to run git branch -a to see which branch you are on before making changes. Along with this, if you checkout into one of the red remote branches, YOU WILL NOT BE WORKING IN/WITH THE BRANCH, you will just have pulled the most recent commit. This brings its own implications, so read up and work accordingly.
<br />

## Workflow
Begin with 
```
git status
```
If nothing has changed in your directory, commandline will tell you as such. Create a file: `Echo Hello World > "File.txt"`.
This will create the new text file File.txt, in your respective filesystem directory. run `git status` again.

> **Note** Remember pull changes first before beginning your work. You'll see what im talking about below.

### **Staging**
'File.txt' is currently denoted by red to note that it has been changed. Git however, does not know if this change
is accidental or temporary, such as if the file is currently being worked on, so it is simply noted through color. If the change
is purposeful, mark the change by running
```
git add <file name>
```
to stage the file, so the change is now accepted. Running `git status`, it should now show up as green.

If you wish to stage all files changed, run
```
git add .
```
To revert/unaccept staged (added) files, run 
```
git reset HEAD <file name>
```

### **Committing**
After files are in the staging area, you may now officially publish them to the local repository, in this case, the branch we created earlier.
This marks the change for anyone else on the project, or the public (depending on your git installation, and when pushing), to see.

To commit changes, run
```
git commit -m 'type a comment in here to document what changes youve made, or leave it empty'
```

### **Publishing**
After any necessary commits have been made to your local repository, you may now publish the updated commits/repository to an online 
service, through the use of git push command. This will update the online service hosting your repository, with your new changes.

To push, run
```
git push origin <branch name>
``` 
Respective credentials will be brought up following the execution of this command.

> **Note** If you receive an error denoting a missing 'origin', run
`git remote add origin <repository url>`
This specifies the "origin" of the repository/project online for your 
local git to reference when pushing and pulling changes. If you've already a remote, run
`git remote set-url origin <repository url>`. This will update your remote to the repository
at hand.

### **Pulling**
If you wish to download updates from a published repository (already established on your local machine), run
```
git pull
```
This will download any changes made to the repository to your local directory, and notify you of the changes.

After a branch is finalized, if you have (ACCESS or AUTHORIZATION)!! to the master branch, to merge, switch to the master branch, and WHEN READY, run
```
git merge <branch name>
```
when you are ready to push the updates to a public repository such as to update Github, run
```
git push origin master
```
to update the master branch. You may now delete the branch on the local repository: to do so on the public repository, run
```
git push origin --delete <branch name>
```
or keep working in the branch if necessary
<br />
<br />
<br />
<br />
<br />

# Further Reading
This subsection is designed to inform readers of useful applications in git that I've found beneficial to my workflow. You'll of course find more than I could list by referencing the manual, found here: https://git-scm.com/docs.

### **Gitignore**
In your directory, run
```
touch .gitignore
```
This command will create a file which, when listing the names of files, one file name per line, tells git to ignore them when committing and staging. 
These files will not show up in `git status` and will be entirely absent from the development process done in git. 
The same applies for directories, however instead of simply a line containing a file name such as
```
File.txt
```
you instead type in `/<directory name>`, as so
```
File.txt
/directory
```
Such a file will have git ignore File.txt and the directory or folder (including subcontents) named 'directory' for any changes made to them, as well as for
staging and committing.
<br />

### **Log**
When in a branch, if you run
```
git log --oneline
```
You will be shown the commits and their given comments/documentations.

### **Updating Branch**
Should you have a branch you need to update with updates from the online repository, 
run
```
git pull origin <main/master>

### **Security**
[Add an SSH key to your Github 
account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
<br />
[Verify yourself by signing (signature) your commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)
