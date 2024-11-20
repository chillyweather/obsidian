# git stash

[[Knowledge Base/Web Development/GIT & Command Line/git]]

The `git stash` command saves all the changes that were not committed away, so you can continue working on them later.

```bash
git branch
feat/new-header
* main

git stash
Saved working directory and index state WIP on main: 9adbf24 Added bye function
```

### git stash save

The `git stash save stash_message` command adds a description of changes made. It's convenient when there are a lot of them, and it's hard to remember the exact branch and the last commit.

```bash
git stash save "Changed title in index.html"
Saved working directory and index state On main: 
Changed title in index.html
```

The `git stash list` command lists all the stash entries, with the names of the branches where stashed changes were made, and a short description of these changes:

```bash
git stash list

stash@{0}: WIP on main: 9adbf24 Added bye function ## Changes stashed in main
stash@{1}: WIP on feat/new-header: b6e5dd3 Added style.css ## Changes stashed in develop
```

Use the `git stash apply stash@{n}` or `git stash apply n` command to retrieve the changes from `main`; replace `n` with the stash entry number according to the list

```bash
git branch
feat/new-header
* main

git stash list
stash@{0}: WIP on main: 9adbf24 Added bye function # we want to retrieve these changes
stash@{1}: WIP on feat/new-header: b6e5dd3 Added style.css

git stash apply stash@{0} # retrieved the changed title to main

Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
```

### git stash clear

Use the `git stash clear` command to clear the stash list and keep everything in order

```bash
git stash clear
git stash list
# empty
```

### git stash pop

`git stash pop` **throws away** the (topmost, by default) stash after applying it, whereas `git stash apply` **leaves it in the stash list** for possible later reuse (or you can then `git stash drop` it).