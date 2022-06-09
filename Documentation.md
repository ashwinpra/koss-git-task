# Some new git commands

---

## `git stash`	

- Saves your code without making a commit! 
- When it's run, uncommited code disappears without being commited. 
- It's basically like storing a local commit to your branch, which cannot be pushed to a remote repository so it's for personal use.
- Once you come back and type `git stash list` you will get a list of your local changes, and you can work on it. 
- You can manually push changes to stash using `git stash push -m "<message>"`
- Then you can run `git stash apply` or `git stash apply x` according to your need. (x is corresponding index)
- Lower the index, more recent the change 
- This can be used for debugging of potentially bugged file by stashing it and seeing if there is a bug, if not then checking out. 
- `git stash pop` used to implement that stash on your main code and then remove it from the stash list. 
- You can even carry forward the stashed commits to a different branch using `git stash branch`
- **Note:** Even after applying a stash, it doesn't get deleted, so yo can do it individually by using `git stash drop x` or all by using `git stash clear`.

---

## `git bisect`

- Performs a binary search between two given commits and then display a specific commit's details. 

- You give git a 'good' commit and a 'bad' commit and it finds what the bug was in the bad commit, as compared to the good one. 

- Go to the buggy branch, go through its commits to find a good commit, and compare it with the bad one to find the bug. 

- Run `git log` to get a list of commits to choose from. 

- Then run the following: 

  ```bash
  git bisect start 
  git bisect bad <bad-commit-id>
  git bisect good <good-commit-id>
  ```

- If after running, the issue still persists, we use `git bisect bad` (only that much)

- We will need to repeat this step until git has traversed all the possible steps.

- Once you get the first bad commit (ie last good commit) finally, `git bisect good`.

- Once it's found, run `git show <commit-id>` to see the bad commit itself. 

- Once finished, you can run `git bisect reset` to reset the branch back to last good commit.

- You can reset to the last good commit by `git revert <commit-id>`, then type `wq` -> **check this**

---

## `git reflog`

- Used to access a list of checkpoints that is maintained by Git. 

- it can be used to undo merges, recover lost commits/branches, etc. 

- The main difference between `reflog` and `log` is that `log` gives accounts of the public repository's details whereas `reflog` gives all accounts of the repository's changes and commits on the user's local system. 

  ​	

---

## `git diff`

- To see the difference between commits - current commit and staged/unstaged commit. 
- Can also be used to see differences between two branches
- `git diff` for unstaged changes, `git diff --staged` for staged changes, `git diff branch1 branch2`for difference between two branches.

---

## `git switch`

- To switch to another branch.
- `git switch branch-name` used to switch to a certain branch. 
- `git switch -` used to switch back to original branch.

---

## `git rebase`

- To reapply commits on top of another base tip 
- Usually used instead of `git merge` to get a linear history. 
- In the case of `merge` it creates a branched structure that ties together both branches, whereas here in `rebase` it creates a linear branch by moving the entire branch being rebased to begin on the tip of the `main` branch by rewriting all the commits in the original branch
- This is usually just used in private projects as the commits in `main` branch is moved to the original branch, so the `main` branch still remains intact for all the developers working on the branch.

---

## `git cherry-pick`

- Used to pick changes from one branch and apply it to current branch 
- This is usually done before merging branches. 
- `git cherry-pick <commit>`
- add `-n` prefix at the end to stage the changes, but not commit