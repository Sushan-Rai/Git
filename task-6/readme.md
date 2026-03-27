6. **Stashing Changes for Context Switching**
    
    **Objective:**
    
    - Learn how to use Git stash to save uncommitted work temporarily.
    
    **Requirements:**
    
    - Make changes in your working directory without committing.
    - Use `git stash` to save these changes.
    - Switch branches, perform some work, then return and reapply your stashed changes with `git stash pop`.
    - Optionally, demonstrate how to view and manage multiple stashes using `git stash list` and `git stash drop`.

    **Execution**

    - - PS E:\presidio-self-learning\Git> git status
    On branch main
    Your branch is up to date with 'origin/main'.

    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
            new file:   task-6/file.txt

    - PS E:\presidio-self-learning\Git> git checkout task6feature
    error: Your local changes to the following files would be overwritten by checkout:
            task-6/file.txt
    Please commit your changes or stash them before you switch branches.
    Aborting
    - PS E:\presidio-self-learning\Git> git stash
    Saved working directory and index state WIP on main: a82a5c0 Task 5: readme updated
    - PS E:\presidio-self-learning\Git> git checkout task6feature
    Switched to branch 'task6feature'
    - PS E:\presidio-self-learning\Git> git stash
    No local changes to save
    - PS E:\presidio-self-learning\Git> git add .                 
    - PS E:\presidio-self-learning\Git> git status
    On branch task6feature
    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
            modified:   task-6/file.txt

    - PS E:\presidio-self-learning\Git> git stash 
    Saved working directory and index state WIP on task6feature: 7e90e4a Task-6: Hotfix on feature
    - PS E:\presidio-self-learning\Git> git checkout main
    Switched to branch 'main'
    Your branch is up to date with 'origin/main'.
    - PS E:\presidio-self-learning\Git> git stash list
    stash@{0}: WIP on task6feature: 7e90e4a Task-6: Hotfix on feature
    stash@{1}: WIP on main: a82a5c0 Task 5: readme updated
    - PS E:\presidio-self-learning\Git> git stash apply "stash@{0}"
    CONFLICT (modify/delete): task-6/file.txt deleted in Updated u- PStream and modified in Stashed changes.  Version Stashed changes of task-6/file.txt left in tree.
    On branch main
    Your branch is up to date with 'origin/main'.

    Unmerged paths:
    (use "git restore --staged <file>..." to unstage)
    (use "git add/rm <file>..." as appropriate to mark resolution)
            deleted by us:   task-6/file.txt

    no changes added to commit (use "git add" and/or "git commit -a")
    - PS E:\presidio-self-learning\Git> git add .
    - PS E:\presidio-self-learning\Git> git stash list
    stash@{0}: WIP on task6feature: 7e90e4a Task-6: Hotfix on feature
    stash@{1}: WIP on main: a82a5c0 Task 5: readme updated
    - PS E:\presidio-self-learning\Git> git commit -m"Task 6: Migrated uncommitted changes from another branch to main"
    [main 87b32f4] Task 6: Migrated uncommitted changes from another branch to main
    1 file changed, 1 insertion(+)
    create mode 100644 task-6/file.txt
    - PS E:\presidio-self-learning\Git> git stash drop "stash@{1}"
    Dropped stash@{1} (bc89aaf5426a2bd4387913662e424e5a5ce51ed0)
    - PS E:\presidio-self-learning\Git> git checkout task6feature
    Switched to branch 'task6feature'
    - PS E:\presidio-self-learning\Git> git stash drop "stash@{0}"
    Dropped stash@{0} (61e57b357ccd8fffc23c7441be0949007c37049d)
    - PS E:\presidio-self-learning\Git> git checkout main
    Switched to branch 'main'
    Your branch is ahead of 'origin/main' by 1 commit.
    (use "git push" to publish your local commits)