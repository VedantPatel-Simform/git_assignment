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
# Practical Exercises


- create new branch from develop
    ```bash
    git checkout develop
    git branch TE-T181
    ```

- add commit message hooks to check if the first letter of the msg is capitalized.
    Hook code:
    ```bash
    #!/bin/bash

    commit_msg_file=$1
    commit_msg=$(cat "$commit_msg_file")

    first_letter=$(echo "$commit_msg" | head -c 1)

    if [[ "$first_letter" =~ [a-z] ]]; then
        echo "Error: The commit message must start with a capital letter."
        exit 1
    fi

    exit 0
    ```

- add multiple commits

- create a pull request
    ```bash
    git push origin TE-T181
    ```

- create another branch
    ```bash
    git branch TE-T181-feature1
    ```
    add commits in this branch

- merge the Pull request with id `TE-T181 PR #1` to `develop` branch
- update the current `develop` branch by pulling the changes from remote branch and then create Pull Request again of current branch.
   ```bash
    git pull origin develop
    ```

    ```bash
    git push origin TE-T181-feature1
    ```
- add tag to latest develop branch
    ``` bash
    git tag -a v1.0.0 -m "my version 1.0.0" 
    ```
