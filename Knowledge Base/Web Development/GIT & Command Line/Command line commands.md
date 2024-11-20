## GIT

### Commands for updating your Git configuration

`git config --global user.name "Practicum Student"` — to set `user.name`, enter your first and last name or alias using Latin letters inside quotation marks `git config --global user.email practicum_student@gmail.com` — replace `practicum_studment@gmail` with your real email address to set the value of `user.email`

`git config --global init.defaultBranch main` — change the default Git branch to `main`

`git config --list` — get a list of all Git configuration properties

### **Commands for synchronizing your local repository with one on GitHub**

`git remote add origin https://github.com/practicum-student/new-repo.git` — when we're in the folder containing your local repository, this will link it to the remote repository (remember to enter your own URL).

`git push -u origin main` — push all files from the local repository to the linked remote repository.

### **Commands to commit the work you want to push**

`git add file_name` — add a single file to be committed by writing its name after `add`.

`git add -A` — use the `-A` flag to add all files.

`git commit -m "commit message"` — make the commit. You should leave a message alongside the commit that will make it easy to understand the changes that were made.

### **Commands to push your commits**

`git pull` — pull changes made by other developers.

`git push` — publish changes to a remote repository.



## Command line

#terminal #commandline

### **Commands**

`pwd` — print the path of the folder that you're in.

`ls` — display a list of files in the current folder.

`cd first-project` — go to the `first-project` folder.

`cd first-project/images` — go to the `images` folder in the `first-project` folder.

`cd ..` — go up one level to the parent folder.

`cd ~` — go to your home directory (that's `/Users/practicum_student` in our case).

`mkdir second-project` — create a folder with the name `second-project` in the current folder.

`rm about.html` — delete `about.html`.

`rmdir images` — delete the `images` folder if it's empty.

`rm -r second-project` — delete the `second-project` folder and everything inside of it.

`touch index.html` — create `index.html` in the current folder.

`touch index.html style.css script.js` — create several files; their names are separated with spaces.

### Branch

```bash
git branch feature/header

git checkout feature/header # switched to the feature/header branch
git branch # checked the current branch
* feature/header 
main
```

Git also allows creating a branch and immediately switching to it. It's done with this command:

```bash
git checkout -b feature/header 
git checkout -b bugfix/horizontal-scroll
```

#### merge branches
```bash
git merge feature/header
```

#### Deleting a branch

```bash
git branch -D shmo
```
