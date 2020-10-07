# A small list of Git hacks
The following list of hacks have been largely sourced from the git documentation pages and Stack Overflow answers.

### Initialize and add to a new repository
	git init
	git add .
	git commit -m <commit message>
	git remote add origin <remote url>.git
	git push origin master

### Make an empty commit (to trigger rebuild)
	git commit --allow-empty -m "Trigger rebuild"

### Amend a recent commit (before push)
	git commit --amend -m '<Amended commit message>'

### Amend a commit (way after push too :wink:)
	git rebase -i HEAD~n 

- Once the default editor pops up, copy the commits on top and change pick to reword.
- If many more commit files open, change the commit files in all of them.
- Force push the amended commits.

```
git push --force
```

### Unstage a recent add
	git reset <file/files to be unstaged> 	(or)
	git reset		(resets everything that has been staged)

### Deal with deleted large files
	git filter-branch --index-filter 'git rm -r --cached --ignore-unmatch <file/dir>' HEAD

### Revert HEAD back by a few commits
	git revert HEAD~<number of commits to go back>

### Force pull from a repository
	git fetch --all
	git reset --hard origin/<branch_name>

### Get remote URL
	git remote show origin

### Remove sensitive data
	git filter-branch --force --index-filter "git rm --cached --ignore-unmatch PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA" --prune-empty --tag-name-filter cat -- --all
