# GIT

## Actions

### Status

Check the status of the current state.

* Status: `git status`
* Log: `git log`

### Update local repo

* Fetch: `git fetch`
* Pull: `git pull`

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

Remember the 'best practises' presented earlier. Try to create a good
and meaningful commit message. Save and close the editor.

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
