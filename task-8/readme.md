8. **Using Git Hooks for Automated Checks**
    
    **Objective:**
    
    - Set up a Git hook to run scripts (like linters or tests) before commits are finalized.
    
    **Requirements:**
    
    - Create a `pre-commit` hook in the `.git/hooks` directory.
    - Write a simple script (e.g., a shell script or Node script) that runs a linter or a unit test.
    - Ensure that if the tests or linting fail, the commit is aborted.
    - Document how Git hooks can improve code quality in collaborative projects.

    **Execution**
    - PS E:\presidio-self-learning\Git> git status
    On branch main
    Your branch is up to date with 'origin/main'.

    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
            new file:   task-8/test.js

    - PS E:\presidio-self-learning\Git> git status
    On branch main
    Your branch is up to date with 'origin/main'.

    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
            new file:   task-8/test.js

    - PS E:\presidio-self-learning\Git> git commit -m "Task 8: removed console.log and pre-commit git hook"
    Running checks...
    All checks passed
    [main 0fba08e] Task 8: removed console.log and pre-commit git hook
    1 file changed, 3 insertions(+)
    create mode 100644 task-8/test.js
    - PS E:\presidio-self-learning\Git> git add .
    - PS E:\presidio-self-learning\Git> git commit -m "Task 8: added console.log and pre-commit git hook"  
    Running checks...
    console.log found in task-8/test.js
    - PS E:\presidio-self-learning\Git> git restore --staged task-8/test.js

    - Git Hooks like pre-commit can be useful to check code quality or put certain restrictions on how the code should look like before committing which can help enforce code guidelines while collaborating on projects

    **Script**

    ```
    #!/bin/sh

    echo "Running checks..."

    FILES=$(git diff --cached --name-only --diff-filter=ACM | grep '\.js$')

    for file in $FILES
    do
    if grep -q "console.log" "$file"; then
        echo "console.log found in $file"
        exit 1
    fi
    done

    echo "All checks passed"
    exit 0
    ```
