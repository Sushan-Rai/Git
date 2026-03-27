9. **Working with Remote Repositories and Collaboration**
    
    **Objective:**
    
    - Simulate a collaborative workflow with remote repositories.
    
    **Requirements:**
    
    - Create a local repository and push it to a remote service (e.g., GitHub or GitLab).
    - Create a feature branch, make commits, and push the branch to the remote.
    - Open a Pull Request (or Merge Request) and perform a code review process.
    - Merge the feature branch into the main branch on the remote and then pull the changes locally.

    **Execution**

    - PS E:\presidio-self-learning\Git> git add task-9/random.txt
    - PS E:\presidio-self-learning\Git> git commit -m "Task 9: added a random text file"
    Running checks...
    All checks passed
    [main 2ccbb33] Task 9: added a random text file
    1 file changed, 1 insertion(+)
    create mode 100644 task-9/random.txt
    - PS E:\presidio-self-learning\Git> git push -u origin main
    Enumerating objects: 5, done.
    Counting objects: 100% (5/5), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (4/4), 345 bytes | 345.00 KiB/s, done.
    Total 4 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
    remote: Resolving deltas: 100% (1/1), completed with 1 local object.
    To https://github.com/Sushan-Rai/Git.git
    b8cc5be..2ccbb33  main -> main
    branch 'main' set up to track 'origin/main'.
    - PS E:\presidio-self-learning\Git> git remote show origin
    * remote origin
    Fetch URL: https://github.com/Sushan-Rai/Git.git
    Push  URL: https://github.com/Sushan-Rai/Git.git
    HEAD branch: main
    Remote branches:
        feature tracked
        main    tracked
    Local branches configured for 'git pull':
        feature merges with remote feature
        main    merges with remote main
    Local refs configured for 'git push':
        feature pushes to feature (up to date)
        main    pushes to main    (up to date)
    - PS E:\presidio-self-learning\Git> git checkout -b feature-login
    Switched to a new branch 'feature-login'
    - PS E:\presidio-self-learning\Git> git add task-9/random.txt
    - PS E:\presidio-self-learning\Git> git commit -m "Task 9: updated random text file"
    Running checks...
    All checks passed
    [feature-login b1375d3] Task 9: updated random text file
    1 file changed, 2 insertions(+), 1 deletion(-)
    - PS E:\presidio-self-learning\Git> git push -u origin feature-login
    Enumerating objects: 7, done.
    Counting objects: 100% (7/7), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (4/4), 364 bytes | 364.00 KiB/s, done.
    Total 4 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
    remote: Resolving deltas: 100% (1/1), completed with 1 local object.
    remote:
    remote: Create a pull request for 'feature-login' on GitHub by visiting:
    remote:      https://github.com/Sushan-Rai/Git/pull/new/feature-login
    remote:
    To https://github.com/Sushan-Rai/Git.git
    * [new branch]      feature-login -> feature-login
    branch 'feature-login' set up to track 'origin/feature-login'.
    - PS E:\presidio-self-learning\Git> git checkout main
    Switched to branch 'main'
    Your branch is up to date with 'origin/main'.
    - PS E:\presidio-self-learning\Git> git pull origin main
    remote: Enumerating objects: 1, done.
    remote: Counting objects: 100% (1/1), done.
    remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
    Unpacking objects: 100% (1/1), 920 bytes | 920.00 KiB/s, done.
    From https://github.com/Sushan-Rai/Git
    * branch            main       -> FETCH_HEAD
    2ccbb33..4cf7565  main       -> origin/main
    Updating 2ccbb33..4cf7565
    Fast-forward
    task-9/random.txt | 3 ++-
    1 file changed, 2 insertions(+), 1 deletion(-)