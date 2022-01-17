# Git

Source: Notes
Status: Unprocessed

```jsx
#1 Discard all local changes in a file
git restore <filename>

#2 Restoring a deleted file
git restore <filename>

#3 Discarding Chunks / Lines in a file
git restore -p <filename>

#4 Discarding all local changes
git restore .

#5 Fixing the Last commit
git commit --amend -m "correct"

#6 Reverting a commit in the module
git revert 2b504bee

#7 Resetting to an old revision
git reset --hard 2b54bee
git reset --mixed 2b54bee

#8 Resetting a file to an old revision
git restore --source 2b54bee index.html

#9 Recovering deleted commits
git reflog
git branch happy-ending 2b54bee

#10 Recovering a deleted branch
git reflog
git branch develop 2b54bee

#11 Moving a commit to a new branch
git branch feature/login
git reset HEAD~1 --hard

#12 Moving a commit to a different branch
git checkout feature/newsletter
git cherry-pick <SHA>
git checkout master
git reset --hard HEAD~1

#13 Editing old  commit messages
git rebase -i HEAD~3
..then use "reword" option

#14 Deleting old  commits
git rebase -i HEAD~3
..and remove lines for unwanted commits

#15 Squashing multiple commits into one
git rebase -i HEAD~3
..then use "squash" option

#16 Adding a change to an old commit
git commit --fixup 2b504bee
git rebase -i --autosquash HEAD~3
```

#17 Splitting / Editing an old commit

![Git%20006898d8f79d4e3290be3f9e3b9284ae/17-1.jpg](Git%20006898d8f79d4e3290be3f9e3b9284ae/17-1.jpg)

![Git%20006898d8f79d4e3290be3f9e3b9284ae/17-2.jpg](Git%20006898d8f79d4e3290be3f9e3b9284ae/17-2.jpg)

![nse-8344671420616985038-186975.jpg](Git%20006898d8f79d4e3290be3f9e3b9284ae/nse-8344671420616985038-186975.jpg)