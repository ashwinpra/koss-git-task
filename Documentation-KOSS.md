<h1>Documentation</h1>

## `git stash`	

- Saves your code without making a commit! 
- When it's run, uncommited code disappears without being commited. 
- It's basically like storing a local commit to your branch, which cannot be pushed to a remote repository so it's for personal use.
- Once you come back and type `git stash list` you will get a list of your local changes, and you can work on it. 
- Then you can run `git stash apply` or `git stash apply stash@{x}` according to your need. 
- If you don't need to apply those changes, then just use `git checkout . ` which resets all the uncommited code. 
- This can be used for debugging of potentially bugged file by stashing it and seeing if there is a bug, if not then checking out. 
- You can even carry forward the stashed commits to a different branch using `git stash branch`
- **Note:** Even after applying a stash, it doesn't get deleted, so yo can do it individually by using `git drop` or all by using `git stash clear`.

## `git bisect`

- Performs a binary search between two given commits and then display a specific commit's details. 

- You give git a 'good' commit and a 'bad' commit and it finds what the bug was in the bad commit, as compared to the good one. 

- Go to the buggy branch, go through its commits to find a good commit, and compare it with the bad one to find the bug. 

- Run `git log` to get a list of commits to choose from. 

- Then run the following: 

  ```bash
  git bisect start 
  git bisect bad <commit-id>
  git bised good <commit-id>
  ```

- If after running, the issue still persists, we use `git bisect bad` (only that much)
- We will need to repeat this step until git has traversed all the possible steps. 
- Once it's found, run `git show` to see the bad commit itself. 
- Once finished, you can run `git bisect reset` to reset the branch back to normal working state. 

## `git reflog`

## `git diff`

## `git switch`

## `git rebase`

## `git cherry-pick`