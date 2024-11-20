# CHANGE COMMIT MESSAGE

If you screw up a commit message, you can change it with the `--amend` flag. For example:

```bash
# Change the last commit message
git commit --amend -m "A: add contents.md"
```


# LOG

Use the `-n` and `--no-pager` options to limit the maximum number of commits shown, and more importantly, to run it without the interactive pager. E.g.:

```bash
git --no-pager log -n 10
```


# CAT FILE

Luckily, Git has a built-in plumbing command, [cat-file](https://git-scm.com/docs/git-cat-file), that allows us to see the contents of a commit without needing to futz around with the object files directly.

```
git cat-file -p <hash>
```

```bash
git cat-file -p 98572a9058420b25f5fe6f5f210f552edf7c038b

#tree 8beea9fad8fce5b26672acaaf0bd02987b90ae93
#author Dmitri Dmitriev <d.dzmitryeu@gmail.com> 1716096509 +0300
#§committer Dmitri Dmitriev <d.dzmitryeu@gmail.com> 1716096509 +0300

  

#A: add contents.md
```


# GIT CONFIG

There are several locations where Git can be configured. From more general to more specific, they are:

- **system**: `/etc/gitconfig`, a file that configures Git for all users on the system
- **global**: `~/.gitconfig`, a file that configures Git for all projects of a user
- **local**: `.git/config`, a file that configures Git for a specific project
- **worktree**: `.git/config.worktree`, a file that configures Git for part of a project

# RENAME BRANCH

```bash
git branch -m oldname newname
```

# [Change git init default branch name](https://superuser.com/questions/1419613/change-git-init-default-branch-name)

```bash
git config --global init.defaultBranch main
```


# NEW BRANCH

You should already be on the `main` branch: your "default" branch. You can always check with `git branch`.

## TWO WAYS TO CREATE A BRANCH

```bash
git branch my_new_branch
```

This creates a new branch called `my_new_branch`. The thing is, I rarely use this command because usually I want to create a branch and switch to it immediately. So I use this command instead:

```bash
git switch -c my_new_branch

```

# NEW BRANCH FROM SPECIFIC COMMIT

```bash
git switch -c update_dune COMMITHASH
```

# DELETE BRANCH

```bash
git branch -d add_classics
```


# LOG FLAGS

As you know, `git log` shows you the history of commits in your repo. There are a few flags I like to use from time to time to make the output easier to read.

The first is [--decorate](https://git-scm.com/docs/git-log#Documentation/git-log.txt---decorateshortfullautono). It can be one of:

- `short` (the default)
- `full` (shows the full ref name)
- `no` (no decoration)

Run `git log --decorate=full`. You should see that instead of just using your branch name, it will show the full ref name. A [ref](https://git-scm.com/book/en/v2/Git-Internals-Git-References) is just a pointer to a commit. All branches are refs, but not all refs are branches.

Run `git log --decorate=no`. You should see that the branch names are no longer shown at all.

The second is [--oneline](https://git-scm.com/docs/git-log#Documentation/git-log.txt---oneline). This flag will show you a more compact view of the log. I use this one all the time, it just makes it so much easier to see what's going on.

```bash
git log --oneline
```

Run 
```bash
git log --oneline --graph --all
```
 and you should see a nice ASCII art representation of your commit history.


# UNDOING CHANGES

## GIT RESET

The [git reset](https://git-scm.com/docs/git-reset) command can be used to reset any changes in the index (staged but not committed changes) and the worktree (unstaged and not committed changes).

```bash
git reset --hard
```

This is useful if you just want to discard all your current changes and go back to the last commit.

## RESET TO A SPECIFIC COMMIT

If you want to reset back to a specific commit, you can use the [git reset --hard](https://git-scm.com/docs/git-reset) command and provide a commit hash. For example:

```bash
git reset --hard a1b2c3d
```

# ADDING A REMOTE

In git, another repo is called a "remote." The standard convention is that when you're treating the remote as the "authoritative source of truth" (such as GitHub) you would name it the "origin".

By "authoritative source of truth" we mean that it's the one you and your team treat as the "true" repo. It's the one that contains the most up-to-date version of the accepted code.

# COMMAND SYNTAX

```bash
git remote add <name> <uri>
```

```bash
git remote add origin https://github.com/your-username/webflyx.git
```

# FETCH

Adding a remote to our Git repo does _not_ mean that we automagically have all the contents of the remote. First, we need to [fetch](https://git-scm.com/docs/git-fetch) the contents.

## COMMAND

```bash
git fetch
```

This downloads copies of all the contents of the `.git/objects` directory (and other book-keeping information) from the remote repository into your current one.


# LOG REMOTE

The `git log` command isn't only useful for your _local_ repo. You can log the commits of a _remote_ repo as well!

```bash
git log remote/branch
```

For example, if you wanted to see the commits of a branch named `primeagen` from a remote named `origin` you would run:

```bash
git log origin/primeagen
```

# MERGE REMOTE

Just as we merged branches within a single local repo, we can also merge branches between local and remote repos.

## SYNTAX

```bash
git merge remote/branch
```

For example, if you wanted to merge the `primeagen` branch of the remote `origin` into your local `main` branch, you would run this inside the local repo while on the `main` branch:

```bash
git merge origin/primeagen
```


# GIT PUSH

The `git push` command pushes (sends) local changes to any "remote" - in our case, GitHub. For example, to push our local `main` branch's commits to the remote `origin`'s `main` branch we would run:

```bash
git push origin main
```

# PULL

Fetching is nice, but most of the time we want the _actual file changes_ from a remote repo, not just the metadata.

## COMMAND SYNTAX

`git pull [<remote>/<branch>]`

The syntax `[...]` means that the bracketed remote and branch are optional. If you execute git pull without anything specified it will pull your current branch from the remote repo.


# WORKFLOW EXAMPLE

We've covered a lot of Git basics. There's certainly more you can learn, but this will give you a solid foundation to work with as a developer. If you want more, there will be a part 2 of this course released soon where we'll cover more advanced topics.

All that said, I want to leave you with a note on my simple workflow. 90% Of the time, you're only using a handful of git commands to get your coding work done.

## KEEP STUFF ON GITHUB

I keep all my serious projects on GitHub. That way if my computer explodes, I have a backup, and if I'm ever on another computer, I can just clone the repo and get back to work.

## REBASE VS MERGE

I've configured Git to rebase by default on pull, rather than merge so I keep a linear history. If you want to do the same, you can add this to your global Git config:

```
git config --global pull.rebase true
```

![Copy icon](https://www.boot.dev/img/copy_icon.svg)

## MY SOLO WORKFLOW

When I'm working by myself, I usually stick to a single branch, `main`. I mostly use Git on solo projects to keep a backup remotely and to keep a history of my changes. I only rarely use separate branches.

1. Make changes to files
2. `git add .` (or `git add <files>` if I only want to add specific files)
3. `git commit -m "a message describing the changes"`
4. `git push origin main`

It really is that simple for most solo work. `git log`, `git reset`, and some others are of course useful from time to time, but the above is the core of what I do day-to-day.

# MY TEAM WORKFLOW

When you're working with a _team_ Git gets a bit more involved (and we'll cover more of this in part 2 of this course). Here's what I do:

- Update my local `main` branch with `git pull origin main`
- Checkout a new branch for the changes I want to make with `git switch -c <branchname>`
- Make changes to files
- `git add .`
- `git commit -m "a message describing the changes"`
- `git push origin <branchname>` (I push to the _new_ branch name, not `main`)
- Open a [pull request](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests) on GitHub to merge my changes into `main`
- Ask a team member to review my pull request
- Once approved, click the "Merge" button on GitHub to merge my changes into `main`
- Delete my feature branch, and repeat with a new branch for the next set of changes