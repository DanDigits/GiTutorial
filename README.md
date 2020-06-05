# Tutorial
Hi! This repository is an extremely rudimentary introduction into git to help novices, such as myself, begin utilizing git. 
It's purpose is meant to be more pragmatical than informational, so make sure to read up on commands or questions 
you have in order to better familiarize yourself with the service.

This tutorial assumes proficiency in terminal/command line, only insofar of the utilization of command 'cd' and basic knowledge of text editing through terminal using nano/emac/vim/specific respective text editor through command.


## Directories and Modifications
After the creation/location of a new directory/folder, initialize the file into git through
```
git init
```
while terminal/command line is in the file. 

### Cloning
If you wish to begin with already published files, begin by running in terminal
```
git clone <repository url>
```
This will download the repository to one eponymous file in the current directory you find yourself in, and have 
it initialized to be modified by git.

### Branching
After the creation of a local repository, you will find yourself in the 'master' branch of the project, 
which is similar to a main or official directory. When working, its best not to modify the official directory 
until changes can be verified/testd, so we "branch off" with a clone of the main directory for whatever purposes 
needed.

To branch, in the current repository directory, run
```
git branch <new branch name>
```
to create a new branch.

To move between branches, run
```
git checkout <branch name>
```

> **Note** should you remain in the 'master' branch, any modifications you create will modify the repository
everyone sees; should your project be small, this is acceptable, but for large projects with numerous
contruibutors, this is an easy way to disorganize everyone, should a mistake occur. Be Responsible.

#### **Extras**
This subsection is designed to inform readers of extra useful applications in git, to help their workflow. You should
return to this section after reading throughout the entire tutorial, as this will confuse you but is also merely additions
to the lesson, unnecessary for basic use.

##### **Gitignore**
In your directory, run
> touch .gitignore

This command will create a file which should list the names of files, one file name per line, for git to completely ignore. These
files will not show up in `git status` and will be entirely absent from the development process done in git. The same
applies for directories, however instead of simply a line containing a file name such as 
```
new.txt
```
you instead type in `/<directory name>`, as so
```
new.txt
/directory
```
Such a file will have git ignore new.txt and the directory 'directory' for any changes made to them, as well as for
staging and committing.


## Utilization
Begin with 
```
git status
```
If nothing has changed in your directory, command line will tell you as such. Create a file, run `touch new.txt`.
This will create a new text file in the directory. run `git status` again.

### Submitting (`add`)
'new.txt' is currently denoted by red to note that it has been changed. Git however, does not know if this change
is accidental or temporary, as if the file is currently being worked on, so it is simply noted through color. If the change
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
anyone else on the project, or the public, to see.

To committ changes, run
```
git commit
```
After running this command you should see a prompt. This prompt details the files about to be published, for
redundancy, and advises you to submit a comment, to inform what has been done so anyone reading can 
be up to date on the changes.

Should you prefer not to run into this page every time, run
```
git commit -m 'comment'
```
and you will type out your comment in the quotations instead, which will be submitted with your commits after pressing enter.

### Publishing (`push`)
After any necessary commits have been made to your local directory, you may now publish these commits to an online 
directory, through the use of git push command.

When pushing, run
```
git push origin <branch name>
``` 
to push the commits to the repository hosted online. Respective hosting credentials
will be brought up following the execution of this command.


> If you receive an error denoting a missing 'origin', run
```
git remote add origin <repository url>
```
This specifies the "origin" of the repository/project online for your local git to reference when pushing and pulling
changes.

### Updating (`pull`)
If you wish to download updates from your/the published repository, run
```
git pull
```
This will download any changes made to the repository to your local directory, and notify you of the changes.