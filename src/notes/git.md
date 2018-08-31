# GIT

## Actions

### Status

Check the status of the current state.

* Status: `git status`
* Log: `git log`

### Update local repo

* Fetch: `git fetch`
* Pull: `git pull`

### Stashing changes

* Stash changes to stack: `git stash`
* Pop changes from stack: `git stash pop`
* Stash bulkes to stack: `git stash –p`

### Staging

Changed files are marked as `modified`, but the file is not in the
staging area. To be able to commit the change, you need to add the file
to the staging area.

* Add file: `git add <filename>`
* Add current folder: `git add .`
* Add all files: `git add -A`
* Commit and add all files: `git commit -a`

### Commits

Committing files will add the change to the local repository.

* Commit files in staging area: `git commit`
* Commit and add message: `git commit -m "<commit message>"`

Running `git commit` will open the default editor of Git.

#### Best practise for commit messages

* Imperative form
* Wrap the lines to about 72 characters
* Type of commit:
  * feat : A new feature
  * fix : A bug fix
  * docs : Documentation only changes
  * style : Changes that do not affect the meaning of the code
    (white-space,formatting, missing semi-colons, etc)
  * refactor : A code change that neither fixes a bug nor adds a feature
  * perf : A code change that improves performance
  * test : Adding missing tests
  * chore : Changes to the build process or auxiliary tools and
    libraries such as documentation generation
* Structure:

  ```
    <type of commit>: Short (50 chars or less) summary of changes
    
    More detailed explanatory text, if necessary. Wrap it to
    about 72 characters or so. In some contexts, the first
    line is treated as the subject of an email and the rest of
    the text as the body. The blank line separating the
    summary from the body is critical (unless you omit the body
    entirely); tools like rebase can get confused if you run
    the two together.
    
    Further paragraphs come after blank lines.
    - Bullet points are okay, too
    - Typically a hyphen or asterisk is used for the bullet, preceded 
      by a single space, with blank lines in between, but conventions 
      vary here
  ```

#### Change default editor

```
    git config --global core.editor "<path-to-editor>"
```

## Update the remote repository

Run `git push` to push your changes to the remote branch.

### Branching

Create branches for developing.

* List (local) branches: `git branch`
* Create branch: `git branch <your-branch-name>`
* Checkout branch: `git checkout <your-branch-name>`
* Checkout and create branch: `git checkout -b <your-branch-name>`.

For adding the branch to the remote repository (origin). Run:

```
    git push --set-upstream origin <your-branch-name>
```

### Amending to the last commit

To change the most recent commit in the current branch, use the option
`--amend`.

```
    git commit --amend
```

> Note that you need to add the changes you want to include, or run
> commit with the `-a` option to include all changes, just like you
> would with a normal commit.
