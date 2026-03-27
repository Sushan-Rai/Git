3. **Undoing Changes and Reverting Commits**
    
    **Objective:**
    
    - Experiment with undoing changes in your working directory and commits.
    
    **Requirements:**
    
    - Modify a tracked file and use `git checkout -- <file>` (or `git restore`) to undo changes.
    - Make a commit, then use `git revert` or `git reset` to see how you can undo a commit safely.
    - Explain the differences between these approaches.

    **Execution**

    - Modified a tracked file file1.txt and used `git restore task-3/file1.txt` to undo changes added.
    - Made a commit with changes and then used `git revert HEAD` to undo the changes safely.
    - `git restore` works on uncommitted changes that are added and are tracked, and it works on the current working directory while `git revert` worked on commits and creates a new commit whenever it reverts back, `git reset` goes to that particular commit which is before the existing one.