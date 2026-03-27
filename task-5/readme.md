5. **Interactive Rebasing for Clean Commit History**
    
    **Objective:**
    
    - Use interactive rebase to tidy up your commit history.
    
    **Requirements:**
    
    - Create a series of commits (some with minor changes or typos in commit messages).
    - Run `git rebase -i HEAD~n` (with `n` representing the number of commits) to squash, reorder, and edit commit messages.
    - Explain how squashing helps in cleaning up commit history before merging into a main branch.

    **Execution**

    - PS E:\presidio-self-learning\Git> git add .
    - PS E:\presidio-self-learning\Git> git commit -m "Task 5: line1 added"
    [main a36f3c8] Task 5: line1 added
    2 files changed, 12 insertions(+)
    create mode 100644 task-5/file.txt
    create mode 100644 task-5/readme.md
    - PS E:\presidio-self-learning\Git> git add .
    - PS E:\presidio-self-learning\Git> git commit -m "Task 5: line2 added"
    [main fd5f89c] Task 5: line2 added
    1 file changed, 2 insertions(+), 1 deletion(-)
    - PS E:\presidio-self-learning\Git> git add .
    - PS E:\presidio-self-learning\Git> git commit -m "Task 5: line3 added"
    [main f2a10fd] Task 5: line3 added
    1 file changed, 2 insertions(+), 1 deletion(-)
    - PS E:\presidio-self-learning\Git> git log --oneline
    f2a10fd (HEAD -> main) Task 5: line3 added
    fd5f89c Task 5: line2 added
    a36f3c8 Task 5: line1 added
    e0ff791 (origin/main) Task 4: Update readme.md_2
    84cbc75 Task 4: Update readme.md
    bb4b633 (feature1) Task 4: changing from feature1
    dfe07aa Task 4: Initial Commit
    7677e13 Task 3: added readme.md
    2352e0b Task 3: Reverted changes
    936bc4e Task 3: Made some changes to file1
    02e3081 Task 3: Initial commit
    9833be1 Task 2: Added readme
    :
    f2a10fd (HEAD -> main) Task 5: line3 added
    fd5f89c Task 5: line2 added
    a36f3c8 Task 5: line1 added
    e0ff791 (origin/main) Task 4: Update readme.md_2
    84cbc75 Task 4: Update readme.md
    bb4b633 (feature1) Task 4: changing from feature1
    dfe07aa Task 4: Initial Commit
    7677e13 Task 3: added readme.md
    2352e0b Task 3: Reverted changes
    936bc4e Task 3: Made some changes to file1
    02e3081 Task 3: Initial commit
    9833be1 Task 2: Added readme
    - PS E:\presidio-self-learning\Git>
    - PS E:\presidio-self-learning\Git> git rebase -i HEAD~3
    [detached HEAD 4ed745c] Task 5: line1 added
    Date: Fri Mar 27 11:56:37 2026 +0530
    2 files changed, 14 insertions(+)
    create mode 100644 task-5/file.txt
    create mode 100644 task-5/readme.md
    Successfully rebased and updated refs/heads/main.
    - PS E:\presidio-self-learning\Git> git log --oneline
    4ed745c (HEAD -> main) Task 5: line1 added
    e0ff791 (origin/main) Task 4: Update readme.md_2
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
    - PS E:\presidio-self-learning\Git> git status
    On branch main
    Your branch is ahead of 'origin/main' by 1 commit.
    (use "git push" to publish your local commits)

    nothing to commit, working tree clean
    - PS E:\presidio-self-learning\Git> git push -u origin main
    Enumerating objects: 6, done.
    Counting objects: 100% (6/6), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (4/4), done.
    Writing objects: 100% (5/5), 665 bytes | 665.00 KiB/s, done.
    Total 5 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
    remote: Resolving deltas: 100% (1/1), completed with 1 local object.
    To https://github.com/Sushan-Rai/Git.git
    e0ff791..4ed745c  main -> main
    branch 'main' set up to track 'origin/main'.

    - explanation for squashing is basically helps in compressing messy long linear commits into one single understandable commit and become easier while merging and get to know at what point to merge.
