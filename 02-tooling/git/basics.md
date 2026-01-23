
# Basics

## Intro

Linus  Torvalds created Git in 5 days. 

Git commands are mainly divided into high-level(porcelain) and low-level(plumbing). Porcelain commands are used more often by developers, like git add commit push.

Before getting into git we first setup an 'identity' like user.name and user.email

```
git config --get user.name

git config --get user.email
```
Use the above commands if already set to check.

If not set, use the following =

```
git config --add --global user.name "github_username_here"

git config --add --global user.email "email@example.com
```

## Repos

After configuration, first steps usually are creating a repository commonly called repo. A single project can have a Single repo. Repos are like directories which contains project folders and files. 

>Everything about git repos is there in .git


`git init`

this command is just used to create an empty directory or transform a dir into a git repo but empty.

### STATUS

A file can be in 3 stages :-

* untracked

* staged

* committed

#### Untracked

> Deleting untracked files can be painful!

> whenever you make a new file and did whatever you wanted to add in the file, the initial stage is untracked.

#### Staged

`git add <file_name>`

After using this command the file becomes stage in the Index.

>Index is the section where all the files untracked, staged, commited can be visible.

#### Commit

A commit is like a snapshot of the repo at a time, so the changes made get saved in it.

`git commit -m "Your message here"`

<mark>THIS IS LITERALLY THE HALF OF GIT WHICH MOST OF US WILL BE USING IN OUR DAILY LIFE</mark>


### GIT LOG

This shows the version control aspect of git.
This shows who and when they have made commits and changes in the repo.

> Very useful command

`git --no-pager log -n 10`

Here the (no pager) means the output will be shown in the terminal rather than opening a seperate page.

```
git --no-pager log -n 10 --oneline

git --no-pager log -n 10 --oneline --parents

git --no-pager log -n 10 --oneline --parents --graph
```

# HASHES

Each commit has a unique hash. So there are factors which affects the end hash :-

* The commit message
* The author's name and email
* The date and time
* Parent(previous) commit hashes

So to have same hash all the above must happen at same time.(Almost never)

<mark>HASH = SHA</mark>

## Plumbing

All the data in a git repo is stored directly in the `.git/objects`.

> Under the objects dir we can find the hash of our commit in the objects.
>commit is a type of object.

### Note

There is a concept called inode busting in linux OSes. So what happens is there is an inode usage indicator in these os so when the count reaches 100 % , the massive files starts dividing itself to decrease the count of the huge files(inode).

So it takes the first two character of file and makes it a directory.

---

### Cat the commit

When you go to the location of git/objects and eventually reach the commit and then `cat hash` you can see that it is written in gibberish.

This is because the git stores it in raw bytes and that's why git is in small size.

So, Git has its own in-built command `git cat-file -p <hash>`, so this command can read the contents of the file easily.

```
cd .git/objects/e6/778e7169985c41e0c0d9c9b842346594f81ce9

git cat-file -p e6778e7
```
<mark> this is an example case, usually doing cat-file we dont need to put whole hash, just starting 5 letters.</mark>

now the output is :-

> tree 4c42c3e56b05f3b7065a9c426298a89a72585aef

now take this tree hash and cat file it.

The output is :-

> 100644 blob 63778e7169985c41e0c0d9c9b842346594f81ce9    contents.md

when we cat-file the hash in this, its the same as the contents.md.


