4. **Simulating and Resolving Merge Conflicts**
    
    **Objective:**
    
    - Create a scenario that produces a merge conflict and resolve it.
    
    **Requirements:**
    
    - Create two branches from the same commit.
    - Modify the same line(s) of code in a common file in both branches.
    - Attempt to merge the branches, observe the conflict, and resolve it manually.
    - Use `git status` and `git diff` to identify and resolve the conflicting changes.

    **Execution**

    - PS E:\presidio-self-learning\Git> git add .
    - PS E:\presidio-self-learning\Git> git commit -m "Task 4: Initial Commit"
    [main dfe07aa] Task 4: Initial Commit
    2 files changed, 13 insertions(+)
    create mode 100644 task-4/file.txt
    create mode 100644 task-4/readme.md
    - PS E:\presidio-self-learning\Git> git checkout -b feature1
    Switched to a new branch 'feature1'
    - PS E:\presidio-self-learning\Git> git checkout main       
    Switched to branch 'main'
    Your branch is ahead of 'origin/main' by 1 commit.
    (use "git push" to publish your local commits)
    - PS E:\presidio-self-learning\Git> git checkout -b feature2
    Switched to a new branch 'feature2'
    - PS E:\presidio-self-learning\Git> git checkout feature1
    Switched to branch 'feature1'
    - PS E:\presidio-self-learning\Git> git add .
    - PS E:\presidio-self-learning\Git> git commit -m "Task 4: changing from feature1"
    [feature1 bb4b633] Task 4: changing from feature1
    1 file changed, 1 insertion(+), 1 deletion(-)
    - PS E:\presidio-self-learning\Git> git checkout feature2
    Switched to branch 'feature2'
    - PS E:\presidio-self-learning\Git> git add .
    - PS E:\presidio-self-learning\Git> git commit -m "Task 4: changing from feature2"
    [feature2 c9d580d] Task 4: changing from feature2
    1 file changed, 1 insertion(+), 1 deletion(-)
    - PS E:\presidio-self-learning\Git> git merge feature1
    Auto-merging task-4/file.txt
    CONFLICT (content): Merge conflict in task-4/file.txt
    Automatic merge failed; fix conflicts and then commit the result.
    - PS E:\presidio-self-learning\Git> git diff
    - PS E:\presidio-self-learning\Git> git status
    On branch feature2
    nothing to commit, working tree clean
    - PS E:\presidio-self-learning\Git> git main
    git: 'main' is not a git command. See 'git --help'.The most similar command is
            mailinfo
    - PS E:\presidio-self-learning\Git> git checkout main
    Switched to branch 'main'
    Your branch is ahead of 'origin/main' by 1 commit.
    (use "git push" to publish your local commits)
    - PS E:\presidio-self-learning\Git> git merge feature1
    Updating dfe07aa..bb4b633
    Fast-forward
    task-4/file.txt | 2 +-
    1 file changed, 1 insertion(+), 1 deletion(-)
    - PS E:\presidio-self-learning\Git> git push -u origin main
    Enumerating objects: 10, done.
    Counting objects: 100% (10/10), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (7/7), done.
    Writing objects: 100% (9/9), 952 bytes | 317.00 KiB/s, done.
    Total 9 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
    remote: Resolving deltas: 100% (2/2), completed with 1 local object.
    To https://github.com/Sushan-Rai/Git.git
    7677e13..bb4b633  main -> main
    branch 'main' set up to track 'origin/main'.