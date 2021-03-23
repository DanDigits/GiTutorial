# Tutorial
Hi! This repository is an extremely rudimentary introduction into git to help novices, such as myself, learn and become familiarized with its use. 
Its purpose is meant to be more practical than informational, so make sure to read up on commands or questions you may have as you go along.

To start, the files included in this tutorial are meant to help practice the given commands shown below, but are in no way necessary. They're empty anyhow.

This tutorial assumes proficiency with commandline, only insofar of the utilization of command 'cd' and basic knowledge of text editing using nano/emac/vim/specific respective text editor.


## Directories and Modifications
### Cloning
If you wish to begin with already published/public files, begin by running in commandline
```
git clone <repository url>
```
This will download the repository to one eponymous file in the current directory you find yourself in, and have 
it initialized to be modified by git.

#### Initializing
If not, then after the creation or location of a new directory/folder, initialize said folder into git through
```
git init
```
while inside the respective file in commandline. 

### Branching
After the creation of a local repository, you will find yourself in the 'master' branch of the project, 
which is similar to a main or official directory. When working, its best not to modify the official directory 
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

> **Note** Default branch is the 'master' branch. Any modifications you create will modify the files in this repository
until you move branches. Note that commandline filesystem is NOT linked or in any way respective to git filesystem; e.g.
It is possible to be in a different filesystem directory, and submit work to an entirely SEPARATE repository. Make sure to
change branches accordingly.


## Utilization
Begin with 
```
git status
```
If nothing has changed in your directory, commandline will tell you as such. Create a file: `Echo Hello World > "File.txt"`.
This will create the new text file File.txt, in your respective filesystem directory. run `git status` again.

### Submitting (`add`)
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

### Committing
After files are in the staging area, you may now officially publish them to the branch. This marks the change for 
anyone else on the project, or the public (depending on your git installation), to see.

To committ changes, run
```
git commit
```
After running this command you should see a prompt. This prompt details the files about to be published, for
redundancy, and advises you to submit a comment, to inform what has been done so anyone reading can 
be up to date on the changes. Type out your explanation, and hit enter.

### Publishing (`push`)
After any necessary commits have been made to your local repository, you may now publish these commits to an online 
repository, through the use of git push command.

When pushing, run
```
git push origin <branch name>
``` 
to push the commits to the repository hosted online. Respective hosting credentials
will be brought up following the execution of this command.


> **Note** If you receive an error denoting a missing 'origin', run
`git remote add origin <repository url>`
This specifies the "origin" of the repository/project online for your 
local git to reference when pushing and pulling changes. If you've already a remote, run
`git remote set-url origin <repository url>`. This will update your remote to the repository
at hand.

### Updating (`pull`)
If you wish to download updates from a published repository (already established on your local machine), run
```
git pull
```
This will download any changes made to the repository to your local directory, and notify you of the changes.

# **Extras**
This subsection is designed to inform readers of extra useful applications in git, to help their workflow. Currently a work in progress.

##### **Gitignore**
In your directory, run
```
touch .gitignore
```
This command will create a file which should list the names of files, one file name per line, for git to completely ignore. These
files will not show up in `git status` and will be entirely absent from the development process done in git. The same
applies for directories, however instead of simply a line containing a file name such as 
```
File.txt
```
you instead type in `/<directory name>`, as so
```
File.txt
/directory
```
Such a file will have git ignore File.txt and the directory 'directory' for any changes made to them, as well as for
staging and committing.

##### **Comments**
Should you prefer not to run into the page which shows changes, and asks for a comment when pushing comments to a repository, run
```
git commit -m 'comment'
```
and you will be able to type out your comment in the quotations instead. Note however, this wont explicitly show the files that are being committed.
