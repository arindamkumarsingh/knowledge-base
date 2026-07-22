# GIT

### What is git

Git is snapshots not differences of patches etc, it rather stores the whole snapshots of files.

### GIt has integrity

everything is checkummed and stores so it becomes impossible to change the content of the files.
Git uses mechanism called SHA-1 hash and is calculated based on file or directory structure,

### GIt only adds data

After we have commited, we can see experiment with it without worrying about anything

### THe Three states

* Modified - changed a file but not commited to database.

* Staged - marked a modified file to go to ur next commit snapshot.

* Commited - data safely stored in local database.

Working tree - a checkout of a single version of project pulled out from the compressed database in Git dir.

Staging area - a file which holds info of what will go into the next commmit.

Git directory - where git stores metadata and object database. This is what gets cloned .

Workflow-

u modify, then we select what we want to stage for next commit, do a commit.


Mostly all the git commands will be run on the command line only.

## First time git setup

Git has `git config` which helps set configuration variable. THese variables are stored in three diff places:-

1. `[path]/etc/gitconfig` file containes values of every user on system and repos, if we pass `--system` to `git config` it reads from this file but requires superuser priveledge

2. `~/.gitconfig` or `/.config/git/config` - values specific to the user. Can make git read this by passing `--global` and affects all repos u work with system.

3. `config` file in `.git/config` of the repo currently used, its specific to that that repo and this is by default and we need to be in git repo to this option to work properly, u can force by `--local`.

Each level can override the previous level.

to know all the settings and the source.

`git config --list --show-origin`.

### Identity.

when git installed,we set user name and email address as every git commit uses this and its immutable to the commits.

```bash

git config --global user.name "John doe"
git config --global user.email johndoe@example.com
```

U need to do this once and if u want to override this, just use the above without global as it will override the global as discussed above.

After creating a new repo with `git init`. To set main as default branch.

`git config --global init.defaultBranch main`

## Help

```bash
git help <verb>
git <verb> --help
man git-<verb>


```

above are 3 wasy to get man command equivalent.

if not comprehensive man-page then just add `-h` before a command.


# GIt basics

### TO get a git repo

1. take local dir and turn into git repo

2. clone an existing git repo.

#### initializing

```bash
cd go/to/ur/path
```

and

```bash
git init
```

creates a new sub dir called `.git` contains a git reppo skeleton. Nothing is added yet, to start vcs shit, u should do git add to some files and then commit.

## Changes to repo

Tracked files are ones whihc were present in the last snapshot as well as newly staged files- these are the one unmodified, modified or stages.

Untracked files are everything else which were not present in last snapshot

To know which files are in which state use `git status` command.

### Tracking new files

Done by `git add`.

Now lets take a file called Readme.md, so if we write down something, do git add but then u remember something to add
u will make changes, but the file is added so the changes must have already been done, we are wrong.

We will see both readme in to be commited and unstaged also. As git stages the file version u `git add`ed.

So u have to git add again to the latest version.

`git status -s` to make the message more compact.

### ignoring files

If we want to git to ignore a set of files that is produced by the build system.

```bash
cat .gitignore
*.[oa]
*~
```

Firs tline tells to ignore `.o` or `.a` the second line tells to ignore files with `~` which is used by text editors for temporary files.

#### Some paters for gitignore

* Blank lines or lines with `#` are ignored.

* Start pattern with forward slash to avoid recursion.

* End pattern with forward slash to spec a dir.

* Negate a patern with exclamation point.

below is a eg. of gitignore.


```
*.a(ignores all .a files)

!lib.a ( but track lib.a, even if ignoring all .a files)

/TODO (ignore the TODO file in curr dir)

build/ ( ignore all files in dir of build)

doc/*.txt(ignore doc/notes.txt but not doc/server/arch.txt)

doc/**/*.pdf

```

TO view staged and unstaged changes, git status can be a bit vague so we use `git diff` for these 2 questions
What have changed but not staged and what have we staged that we want to commit, git diff shows exactly what lines were added or removed.


