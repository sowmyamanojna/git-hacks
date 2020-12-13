# A small list of Git hacks
The following list of hacks have been largely sourced from the git documentation pages and Stack Overflow answers.

### Initialize and add to a new repository
```git
git init
git add .
git commit -m <commit message>
git remote add origin <remote url>.git
git push origin master
```

### Make an empty commit (to trigger rebuild)
```git
git commit --allow-empty -m "Trigger rebuild"
```

### Amend a recent commit (before push)
```git
git commit --amend -m '<Amended commit message>'
```

### Amend a commit (way after push too :wink:)
```git
git rebase -i HEAD~n 
```

- Once the default editor pops up, copy the commits on top and change pick to reword.
- If many more commit files open, change the commit files in all of them.
- Force push the amended commits.

```git
git push --force
```

### Unstage a recent add
```git
git reset <file/files to be unstaged> 	(or)
git reset		(resets everything that has been staged)
```

### Deal with deleted large files
```git
git filter-branch --index-filter 'git rm -r --cached --ignore-unmatch <file/dir>' HEAD
```
Incase the file has already been commited, the above code would throw an error. Reset the HEAD instead.
```git	
git reset HEAD~
```

### Revert HEAD back by a few commits
```git
git revert HEAD~<number of commits to go back>
```

### Force pull from a repository
```git
git fetch --all
git reset --hard origin/<branch_name>
```

### Get remote URL
```git
git remote show origin
```

### Add a submodule
```git
git submodule add <submodule-url> <path>
```

### Remove sensitive data
```git
git filter-branch --force --index-filter "git rm --cached --ignore-unmatch PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA" --prune-empty --tag-name-filter cat -- --all
```

### Break commits into batches and push them
```git
max=$(git log --oneline|wc -l); for i in $(seq $max -500 1); do echo $i; git push origin master~$i:refs/heads/master; done; git push origin master
```

- The batch size of each of the push can be changed here - `for i in $(seq $max -500 1);`. The value is set to 500 in this case.

### Set default editor for git
```git
git config --global core.editor "subl -n -w"
```
The above code is for Sublime Text. The value inside the quotes can be changed for different editors.
