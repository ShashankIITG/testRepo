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
Till now the code is saved on working git repository, and not on online (e.g., github) repository.

8. `git push origin main`: *here i faced an issue*
~~So, i clone the repository using https, and now i want to push (or, update) repository into origin (i.e., short for original location) main (main branch) using `git push origin main`~~. There are series of problems in this:
	- https based origin location was set. I used `git remote -v` to identify the origin. 
	```
	$ git remote -v
	origin  https://github.com/ShashankIITG/testRepo.git (fetch)
	origin  https://github.com/ShashankIITG/testRepo.git (push)
	```
	- i haven't set PTA (personal access token), which is used to authenticate and access github through https protocol. 
Even after setting up PTA on remote(github) and local machine, i wasn't able to push repository to the origin because https is deprecated. It means that "https should work for cloning still, but not for pushing and doing anything maintenance like stuff".

9. `git remote set-url origin git@github.com:ShashankIITG/testRepo.git `: this update ssh based origin location.

10. `git push origin main`

```
$ git push origin main
To github.com:ShashankIITG/testRepo.git
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'github.com:ShashankIITG/testRepo.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
There are 2 possible solution to this:
	- first use `git pull` and then perform `git push`, such that the remote repo content is intergrated with my local machine repository.
	- force push the local repo using `git push --force origin main`

I will perform the 2nd one, since i am not aware of pull command so far. Also, i am working on test repository and there is nothing for me to loose.

10. `git push --force origin main`: It push changes origin even though the clone was performed using https protocol. 

```
$ git push --force origin main
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 4 threads
Compressing objects: 100% (9/9), done.
Writing objects: 100% (10/10), 2.36 KiB | 49.00 KiB/s, done.
Total 10 (delta 2), reused 1 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), done.
To github.com:ShashankIITG/testRepo.git
 + 4fccb55...60c824f main -> main (forced update)
```

> Now, lets see what happen in origin (github repo).
I could see all the commits i made, including the very first commit i made through github gui.

11. `git status`: this shows that local branch is up to date with origin main
```
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

> Now i will save this file, stage, commit, and push this branch/repo to origin.
12. `git add documentary.md && git commit -m "updated the documentary till 12th point which i am performing on local machine" && git push origin main`

> Now, i won't be able to document the output of this here, since i am in chicken and egg condition. :sweat_smile:

13. `git revert 8d43b9b`: 8d43b9b is the commit hash which i found from github gui.
	- `git log` is a command that can be used to find commit-hash. from here i found the last commit-hash was `8d43b9bffbe7296ca6ee5a7e2b706783d8881849`. So, github gui was should first few digits.

`git revert 8d43b9b` command opens the default editor set for git, and  i have to write the new commit message after the commit-hash line.

14. `git push origin main`: after commit i can directly push the commit. 
> 13th and 14th step won't be present in revert commit, i have to make new commit for that.

15. `git branch`: this will display all the branches

```
$ git branch
*  main
```

16. `git checkout -b feature-fix_headings`: this will create and switch to the newly created branch.

```
$ git checkout -b feature-fix_headings
Switched to a new branch 'feature-fix_headings'
```

> we can delete this branch, 1st move to different branch, and 2nd use `git branch -d feature-fix_headings.

> I am updating the documentary while being in feature branch.

17. 