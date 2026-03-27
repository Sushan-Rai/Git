10. **Comprehensive Workflow with Forced Pushes and RecoveryObjective:Requirements:**
    - Simulate an advanced Git scenario that includes forced pushes, recovering lost commits, and a multi-branch workflow.
    - Create a repository with multiple branches representing features, bug fixes, and releases.
    - Simulate a scenario where a forced push (`git push --force`) is required (for example, after rewriting history with an interactive rebase).
    - Use `git reflog` to locate and recover lost commits after a mistaken force push.
    - Document each step, explaining how and why forced pushes should be handled with care, and how `git reflog` can be a lifesaver.
    - Discuss best practices for collaborating with teams when rewriting history and using force pushes.

    **Execution**
    - PS E:\presidio-self-learning\Git> git add .
    - PS E:\presidio-self-learning\Git> git commit -m "Task 10: Initial Commit"
    Running checks...
    All checks passed
    [main 968e942] Task 10: Initial Commit
    1 file changed, 1 insertion(+)
    create mode 100644 task-10/app.txt
    - PS E:\presidio-self-learning\Git> git checkout -b feature
    Switched to a new branch 'feature'
    - PS E:\presidio-self-learning\Git> git commit -am "Task 10: Feature commit 1"
    Running checks...
    All checks passed
    [feature e8d3b30] Task 10: Feature commit 1
    1 file changed, 2 insertions(+), 1 deletion(-)
    - PS E:\presidio-self-learning\Git> git commit -am "Task 10: Feature commit 2"
    Running checks...
    All checks passed
    [feature a96a42b] Task 10: Feature commit 2
    1 file changed, 2 insertions(+), 1 deletion(-)
    - PS E:\presidio-self-learning\Git> git checkout -b bugfix main
    Switched to a new branch 'bugfix'
    - PS E:\presidio-self-learning\Git> git commit -am "Task 10: Bugfix commit"   
    Running checks...
    All checks passed
    [bugfix aabfbd8] Task 10: Bugfix commit
    1 file changed, 2 insertions(+), 1 deletion(-)
    - PS E:\presidio-self-learning\Git> git push -u origin main
    Enumerating objects: 5, done.
    Counting objects: 100% (5/5), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (4/4), 323 bytes | 323.00 KiB/s, done.
    Total 4 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
    remote: Resolving deltas: 100% (1/1), completed with 1 local object.
    To https://github.com/Sushan-Rai/Git.git
    9b63451..968e942  main -> main
    branch 'main' set up to track 'origin/main'.
    - PS E:\presidio-self-learning\Git> git push origin feature
    Enumerating objects: 11, done.
    Counting objects: 100% (11/11), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (4/4), done.
    Writing objects: 100% (8/8), 640 bytes | 640.00 KiB/s, done.
    Total 8 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
    remote: Resolving deltas: 100% (2/2), completed with 1 local object.
    remote:
    remote: Create a pull request for 'feature' on GitHub by visiting:
    remote:      https://github.com/Sushan-Rai/Git/pull/new/feature
    remote:
    To https://github.com/Sushan-Rai/Git.git
    * [new branch]      feature -> feature
    - PS E:\presidio-self-learning\Git> git push origin bugfix 
    Enumerating objects: 7, done.
    Counting objects: 100% (7/7), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (4/4), 327 bytes | 327.00 KiB/s, done.
    Total 4 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
    remote: Resolving deltas: 100% (1/1), completed with 1 local object.
    remote:
    remote: Create a pull request for 'bugfix' on GitHub by visiting:
    remote:      https://github.com/Sushan-Rai/Git/pull/new/bugfix
    remote:
    To https://github.com/Sushan-Rai/Git.git
    * [new branch]      bugfix -> bugfix
    - PS E:\presidio-self-learning\Git> git checkout feature
    Switched to branch 'feature'
    - PS E:\presidio-self-learning\Git> git rebase -i HEAD~2
    [detached HEAD c8f3eb0] Task 10: Feature committed
    Date: Fri Mar 27 20:56:43 2026 +0530
    1 file changed, 3 insertions(+), 1 deletion(-)
    Successfully rebased and updated refs/heads/feature.
    - PS E:\presidio-self-learning\Git> git push --force origin feature
    Enumerating objects: 7, done.
    Counting objects: 100% (7/7), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (4/4), 340 bytes | 340.00 KiB/s, done.
    Total 4 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
    remote: Resolving deltas: 100% (1/1), completed with 1 local object.
    To https://github.com/Sushan-Rai/Git.git
    + a96a42b...c8f3eb0 feature -> feature (forced update)
    - PS E:\presidio-self-learning\Git> git reflog
    c8f3eb0 (HEAD -> feature, origin/feature) HEAD@{0}: rebase (finish): returning to refs/heads/feature
    c8f3eb0 (HEAD -> feature, origin/feature) HEAD@{1}: rebase (squash): Task 10: Feature committed
    e8d3b30 HEAD@{2}: rebase (start): checkout HEAD~2
    a96a42b HEAD@{3}: checkout: moving from bugfix to feature
    aabfbd8 (origin/bugfix, bugfix) HEAD@{4}: commit: Task 10: Bugfix commit
    968e942 (origin/main, main) HEAD@{5}: checkout: moving from feature to bugfix
    a96a42b HEAD@{6}: commit: Task 10: Feature commit 2
    e8d3b30 HEAD@{7}: commit: Task 10: Feature commit 1
    968e942 (origin/main, main) HEAD@{8}: checkout: moving from main to feature
    968e942 (origin/main, main) HEAD@{9}: commit: Task 10: Initial Commit
    9b63451 HEAD@{10}: commit: Task 9: updated readme.md
    4cf7565 HEAD@{11}: pull origin main: Fast-forward
    2ccbb33 HEAD@{12}: checkout: moving from feature-login to main
    b1375d3 (origin/feature-login) HEAD@{13}: commit: Task 9: updated random text file
    2ccbb33 HEAD@{14}: checkout: moving from main to feature-login
    2ccbb33 HEAD@{15}: commit: Task 9: added a random text file
    - PS E:\presidio-self-learning\Git> git checkout 968e942
    Note: switching to '968e942'.

    You are in 'detached HEAD' state. You can look around, make experimental
    changes and commit them, and you can discard any commits you make in this
    state without impacting any branches by switching back to a branch.

    If you want to create a new branch to retain commits you create, you may
    do so (now or later) by using -c with the switch command. Example:

    git switch -c <new-branch-name>

    Or undo this operation with:

    git switch -

    Turn off this advice by setting config variable advice.detachedHead to false

    HEAD is now at 968e942 Task 10: Initial Commit
    - PS E:\presidio-self-learning\Git> git branch
    * (HEAD detached at 968e942)
    bugfix
    feature
    main