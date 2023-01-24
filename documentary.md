This a document where i will notedown all the command i will work in sequential order.

## 1. `git status`: It provide the status of all the files (e.g., changes to file content, new file created, commit) in the working repository

Here, I am working on the clone of testRepo in my local machine. The status command dictates that README.md file is modified.
```
git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

2. `git add README.md`: It allows the git to track the "README.me" file.
~~no output/print of this command~~

3. `git status`: I again ran git status, and this time it shows that README.md file is now at 'Changes to be committed' step from 'Changes not staged for commit' step.

It seems that the `git add` *stage* the file, and the README.md file is now staged.

```
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        documentary.md
```
Since, i am also maintaining this document. The git status has identified 'documentary.md' file as untracked file. Which basically means, that i also have to perform git add command for this documentary and start the tracking of this file, and stage it (file).

Now i will try restore command, out of curiosity.