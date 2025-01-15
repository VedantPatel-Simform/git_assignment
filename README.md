# git_assignment

### Git Exercise:
  * Create a new repository with a template
  * Initialize git-flow:
    ```bash
    git flow init
    ```
  * Create a feature branch for project setup with the proper Zoho task ID (example: `TP2-T1299_Project_Setup`):
    ```bash
    git flow feature start TP2-T1299_Project_Setup
    ```
  * Create a sub-branch from the project setup branch and perform squash, reset, rebase, and cherry-pick:
    ```bash
    git flow feature start TP2-T1299_Project_Setup_Sub_Branch
    ```

### Git Operations:

- **Squash:**
  - Add multiple commits.
  - To squash commits, use the following command:
    ```bash
    git rebase -i HEAD~N  # (n = number of commits back you want to squash)
    ```

- **Rebase:**
  - On branch `TP2-T1299_Project_Setup_Sub_Branch`, run the following to rebase onto the `TP2-T1299_Project_Setup` branch:
    ```bash
    git rebase TP2-T1299_Project_Setup
    ```
  - On branch `TP2-T1299_Project_Setup`, run the following to rebase onto the `TP2-T1299_Project_Setup_Sub_Branch`:
    ```bash
    git rebase TP2-T1299_Project_Setup_Sub_Branch
    ```
  - This will move the head pointer of the feature branch to the top with the sub-feature branch.

- **Cherry-pick:**
  - To add a commit on the feature branch, first switch to the sub-feature branch.
  - Run the following command to cherry-pick the commit:
    ```bash
    git cherry-pick <commit-id>
    ```
  - This will add the `<commit-id>` on top of the sub-feature branch.

- **Reset:**
  - To reset the state of the repository back to a given commit ID and unstage all the commits done since then, use the following command:
    ```bash
    git reset <commit-id>
    ```
