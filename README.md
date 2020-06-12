# A small list of Git hacks
The following list of hacks have been largely sourced from the git documentation pages and Stack Overflow answers.

### Initialize and add to a new repository
	git init
	git add .
	git commit -m <commit message>
	git remote add origin <remote url>.git
	git push origin master

### Amend a recent commit (before push)
	git commit --amend -m '<Amended commit message>'

### Unstage a recent add
	git reset <file/files to be unstaged> 	(or)
	git reset		(resets everything that has been staged)

### Deal with deleted large files

### Revert HEAD back by a few commits
	git revert HEAD~<number of commits to go back>
