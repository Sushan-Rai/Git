7. **Cherry-Picking Commits Between Branches**
    
    **Objective:**
    
    - Selectively apply a commit from one branch to another using cherry-pick.
    
    **Requirements:**
    
    - Create two branches with distinct commits.
    - Identify a commit on one branch that you want to apply to the other.
    - Use `git cherry-pick <commit-hash>` to apply the commit and handle any conflicts if they arise.
    - Verify the commit history to ensure the cherry-picked commit is present.

    **Execution**

    - PS E:\presidio-self-learning\Git> git checkout -b branch1
    Switched to a new branch 'branch1'
    - PS E:\presidio-self-learning\Git> echo "Feature A" > task-7/file.txt
    - PS E:\presidio-self-learning\Git> git add .
    - PS E:\presidio-self-learning\Git> git commit -m "Task-7: Feature A"
    [branch1 96afbc5] Task-7: Feature A
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 task-7/file.txt
    - PS E:\presidio-self-learning\Git> git checkout -b branch2
    Switched to a new branch 'branch2'
    - PS E:\presidio-self-learning\Git> git checkout main      
    Switched to branch 'main'
    Your branch is up to date with 'origin/main'.
    - PS E:\presidio-self-learning\Git> git branch -d branch2  
    error: the branch 'branch2' is not fully merged
    hint: If you are sure you want to delete it, run 'git branch -D branch2'
    hint: Disable this message with "git config advice.forceDeleteBranch false"
    - PS E:\presidio-self-learning\Git> git branch -D branch2
    Deleted branch branch2 (was 96afbc5).
    - PS E:\presidio-self-learning\Git> git checkout -b branch2
    Switched to a new branch 'branch2'
    - PS E:\presidio-self-learning\Git> echo "Feature B" > task-7/file.txt
    out-file : Could not find a part of the path 'E:\presidio-self-learning\Git\task-7\file.txt'.
    At line:1 char:1
    + echo "Feature B" > task-7/file.txt
    + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
        + CategoryInfo          : OpenError: (:) [Out-File], DirectoryNotFoundException
        + FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.OutFileCommand

    - PS E:\presidio-self-learning\Git> echo "Feature B" > task-7/file.txt
    - PS E:\presidio-self-learning\Git> git add .
    - PS E:\presidio-self-learning\Git> git commit -m "Task 7: Feature B"
    [branch2 4a61f1b] Task 7: Feature B
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 task-7/file.txt
    - PS E:\presidio-self-learning\Git> git checkout branch1
    Switched to branch 'branch1'
    - PS E:\presidio-self-learning\Git> git log --oneline
    96afbc5 (HEAD -> branch1) Task-7: Feature A
    2370f53 (origin/main, main) Task 6: Added readme
    87b32f4 Task 6: Migrated uncommitted changes from another branch to main
    a82a5c0 Task 5: readme updated
    4ed745c Task 5: line1 added
    e0ff791 Task 4: Update readme.md_2
    84cbc75 Task 4: Update readme.md
    bb4b633 (feature1) Task 4: changing from feature1
    dfe07aa Task 4: Initial Commit
    7677e13 Task 3: added readme.md
    2352e0b Task 3: Reverted changes
    936bc4e Task 3: Made some changes to file1
    02e3081 Task 3: Initial commit
    9833be1 Task 2: Added readme
    2c9b96d Task 2: Added gitignore to exclude files in the task
    3610d8a Task 1: Added Readme
    - PS E:\presidio-self-learning\Git> git checkout branch2
    Switched to branch 'branch2'
    - PS E:\presidio-self-learning\Git> git cherry-pick 96afbc5
    warning: Cannot merge binary files: task-7/file.txt (HEAD vs. 96afbc5 (Task-7: Feature A))
    Auto-merging task-7/file.txt
    CONFLICT (add/add): Merge conflict in task-7/file.txt
    error: could not apply 96afbc5... Task-7: Feature A
    hint: After resolving the conflicts, mark them with
    hint: "git add/rm <pathspec>", then run
    hint: "git cherry-pick --continue".
    hint: You can instead skip this commit with "git cherry-pick --skip".
    hint: To abort and get back to the state before "git cherry-pick",
    hint: run "git cherry-pick --abort".
    hint: Disable this message with "git config advice.mergeConflict false"
    - PS E:\presidio-self-learning\Git> git status
    On branch branch2
    You are currently cherry-picking commit 96afbc5.
    (fix conflicts and run "git cherry-pick --continue")
    (use "git cherry-pick --skip" to skip this patch)
    (use "git cherry-pick --abort" to cancel the cherry-pick operation)

    Unmerged paths:
    (use "git add <file>..." to mark resolution)
            both added:      task-7/file.txt

    no changes added to commit (use "git add" and/or "git commit -a")
    - PS E:\presidio-self-learning\Git> git log --oneline
    4a61f1b (HEAD -> branch2) Task 7: Feature B
    2370f53 (origin/main, main) Task 6: Added readme
    87b32f4 Task 6: Migrated uncommitted changes from another branch to main
    a82a5c0 Task 5: readme updated
    4ed745c Task 5: line1 added
    e0ff791 Task 4: Update readme.md_2
    84cbc75 Task 4: Update readme.md
    bb4b633 (feature1) Task 4: changing from feature1
    dfe07aa Task 4: Initial Commit
    7677e13 Task 3: added readme.md
    2352e0b Task 3: Reverted changes
    936bc4e Task 3: Made some changes to file1
    02e3081 Task 3: Initial commit
    9833be1 Task 2: Added readme
    2c9b96d Task 2: Added gitignore to exclude files in the task
    3610d8a Task 1: Added Readme
    - PS E:\presidio-self-learning\Git> 
    - PS E:\presidio-self-learning\Git> cat file.txt
    cat : Cannot find path 'E:\presidio-self-learning\Git\file.txt' because it does not exist.
    At line:1 char:1
    + cat file.txt
    + ~~~~~~~~~~~~
        + CategoryInfo          : ObjectNotFound: (E:\presidio-self-learning\Git\file.txt:String) [Get-Content], ItemNotFoundException
        + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetContentCommand

    - PS E:\presidio-self-learning\Git> cat task-7/file.txt
    Feature B
    - PS E:\presidio-self-learning\Git> git checkout main
    task-7/file.txt: needs merge
    error: you need to resolve your current index first
    - PS E:\presidio-self-learning\Git> git diff
    diff --cc task-7/file.txt
    index 04c5bcf,2b95a30..0000000
    Binary files differ
    - PS E:\presidio-self-learning\Git> git add .
    - PS E:\presidio-self-learning\Git> git status
    On branch branch2
    You are currently cherry-picking commit 96afbc5.
    (all conflicts fixed: run "git cherry-pick --continue")
    (use "git cherry-pick --skip" to skip this patch)
    (use "git cherry-pick --abort" to cancel the cherry-pick operation)

    Changes to be committed:
            modified:   task-7/file.txt

    - PS E:\presidio-self-learning\Git> git cherry-pick --continue
    [branch2 94725b9] Task-7: Feature A
    Date: Fri Mar 27 16:02:26 2026 +0530
    1 file changed, 0 insertions(+), 0 deletions(-)
    - PS E:\presidio-self-learning\Git> git log --oneline      
    94725b9 (HEAD -> branch2) Task-7: Feature A
    4a61f1b Task 7: Feature B
    2370f53 (origin/main, main) Task 6: Added readme
    87b32f4 Task 6: Migrated uncommitted changes from another branch to main
    a82a5c0 Task 5: readme updated
    4ed745c Task 5: line1 added
    e0ff791 Task 4: Update readme.md_2
    84cbc75 Task 4: Update readme.md
    bb4b633 (feature1) Task 4: changing from feature1
    dfe07aa Task 4: Initial Commit
    7677e13 Task 3: added readme.md
    2352e0b Task 3: Reverted changes
    936bc4e Task 3: Made some changes to file1
    02e3081 Task 3: Initial commit
    9833be1 Task 2: Added readme
    2c9b96d Task 2: Added gitignore to exclude files in the task