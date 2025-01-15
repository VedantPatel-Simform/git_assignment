# git_assignment

### Git Exercise:
  * Create a new repository with a template
  * Initialize git-flow:
    ```bash
    git flow init
    ```
    ![Step 1](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/1.png)
  * Create a feature branch for project setup with the proper Zoho task ID (example: `TP2-T1299_Project_Setup`):
    ```bash
    git flow feature start TP2-T1299_Project_Setup
    ```
    ![Step 2](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/2.png)
  * Create a sub-branch from the project setup branch and perform squash, reset, rebase, and cherry-pick:
    ```bash
    git checkout -b TP2-T1299_Project_Setup_Sub_Branch
    ```
    ![Step 3](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/3.png)

### Git Operations:

- **Squash:**
  - Add multiple commits.
  - To squash commits, use the following command:
    ```bash
    git rebase -i HEAD~N  # (n = number of commits back you want to squash)
    ```
    ![Squash](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/4.png)

- **Rebase:**
  - On branch `TP2-T1299_Project_Setup_Sub_Branch`, run the following to rebase onto the `TP2-T1299_Project_Setup` branch:
    ```bash
    git rebase TP2-T1299_Project_Setup
    ```
    ![Rebase Step 1](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/5.png)
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
    ![Cherry-pick](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/6.png)

- **Reset:**
  - To reset the state of the repository back to a given commit ID and unstage all the commits done since then, use the following command:
    ```bash
    git reset <commit-id>
    ```
    ![Reset](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/7.png)

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
    ![Multiple commits](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/8.png)

- create a pull request
    ```bash
    git push origin TE-T181
    ```

- create another branch
    ```bash
    git branch TE-T181-feature1
    ```
    ![Feature 1 Branch](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/9.png)
    add commits in this branch

- merge the Pull request with id `TE-T181 PR #1` to `develop` branch
- update the current `develop` branch by pulling the changes from remote branch and then create Pull Request again of current branch.
   ```bash
    git pull origin develop
    ```

    ```bash
    git push origin TE-T181-feature1
    ```
 ![Pull Request](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/10.png)
- add tag to latest develop branch
    ``` bash
    git tag -a v1.0.0 -m "my version 1.0.0" 
    ```
    ![Tagging](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/11.png)

- create two new branches (3 and 4) namely `TE-T181-feature2` and `TE-T181-feature3`
- edit README in feature2 (i.e 3rd branch) and push them
- cherry pick the last commit to the 4th branch (i.e feature3)
    
    ``` bash
    git switch TE-T181-feature3
    git cherry-pick <commit id>
    ```
    ![Cherry-pick 2](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/12.png)

- change the last commit message to the 4th branch (i.e feature3)
    
    ``` bash
    git rebase -i <commit id>
    ```
    ![Rebase to change commit message](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/13.png)

> after editor opens, change the 'pick' to 'reword' and then close it, then again the editor will open and write the new commit message

- add 3 commits to 4th branch and delete the last commit.
    ```bash
    git reset --hard <commit id of last commit> 
    ```
    -- or
    ```bash
    git reset --hard HEAD~1
    ```
    ![Reset Hard](https://github.com/VedantPatel-Simform/git_assignment/blob/main/screenshots/14.png)
