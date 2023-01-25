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

4. `git restore --staged README.md`: It does not return/print anything. This command move the file back to the step where it is not staged. 

I checked it by running `git status`, and output is shown below
```
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        documentary.md

no changes added to commit (use "git add" and/or "git commit -a")
```
One more thing, as git is a version control system, `git restore` command moved the file to unstaged step, *but will not remove any content/code of the file*.

5. `git add .`: The period after `git add` just stage and track changes of all the files in the working git repository.

~~no output~~

6. `git status` returns that both files are stagged and at the step of 'Changes to be committed'.
```
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md
        new file:   documentary.md
```
Now, lets commit :D

7. `git commit -m "{text}" -m "{additional text}"`: The first "text" is the main/major commit message and the 'additional text' is the optional description of the commit message.

```
git commit -m "performed git few commands on local machine till now" -m "performed git clone, status, add, and restore commands. \n I have also created document where i wrote all the commands i performed."
[main f52969e] performed git few commands on local machine till now
 2 files changed, 57 insertions(+)
 create mode 100644 documentary.md
```

