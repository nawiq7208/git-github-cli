# Basic Bash Commmand / step by step

**Create Project on Local Repository using GIT**

~~Select your project directory and create Project Name~~

1. mkdir project-name

- create folder project-name

2. cd project-name

- moving to current directory project-name

3. code .

- open vscode application

4. ctrl/command + shift + backtick

- open terminal on vscode

5. git init -y

- initialize git

6. git add .

- add all files and folders on git

7. git commit -m "initial commit"

- commit the changes with comment "initial commit"

8. gitmoji -c

- using gitmoji library to select the icon, add title, add comment and commit the changes

- how to use gitmoji :

  [gitmoji](https://github.com/carloscuesta/gitmoji-cli)

**Create Project on Remote Repository/GitHub**

~~Using GitHub CLI on Windows OS or Debian, Ubuntu Linux, Raspberry Pi OS (apt)~~

[GitHub CLI](https://github.com/cli/cli)

Installation for Windows OS :

1. winget install --id GitHub.cli

- if GitHub CLI not install yet on your Windows OS

2. export PATH="$PATH:/C:\Program Files\GitHub CLI"

- add to path of bash (run on bash command)

Installation for Debian, Ubuntu Linux, Raspberry Pi OS (apt) :

1. type -p curl >/dev/null || (sudo apt update && sudo apt install curl -y)
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y

2. sudo apt update 

3. sudo apt install gh

Next Installation : 

1. create classic token API on your GitHub account at [Settings](https://github.com/settings/tokens)

- copy paste and save your token API

2. gh auth login

- access using SSH and token

3. gh auth logout

- logout from remote repository

4. gh repo create repository-name (create new repository on GitHub)

- You can also provide additional options like --public or --private to specify the repository's visibility, and --description to set a description.

5. After create your repository than execute this script on your terminal :

- git init
- git add README.md
- git commit -m "chore:first commit"
- git branch -M master
- git remote add origin git@github.com:username/repository-name.git
- git push -u origin master

6. git remote add origin git@github.com:username/repository-name.git

- add remote to your active repository

7. git branch

- Check Existing Branches

8. git fetch origin

- Fetch Branches from Remote Repository

9. git checkout -b new-branch-name

- a single command that combines branch creation and switching to the new created branch using the -b flag

- Remember that creating a new branch allows you to work on a new feature or bug fix without affecting the main development line. You can make changes, commit them to the new branch, and then merge the branch back into the main branch (e.g., master or develop) when the changes are ready.

10. git branch -M develop

- The command git branch -M develop is used to rename the current branch to develop. This command is often used when you want to change the name of the current branch, typically when you are working with the default branch of a Git repository and you want to rename it. The -M flag stands for "move" and indicates that you want to move or rename the branch. The develop argument specifies the new name you want to give to the branch.

11. git push -u origin develop

- Push to Remote Repository, Push your local commits to the remote repository on the main (or master or develop) branch (replace main with the appropriate branch name if needed). The -u flag sets the upstream branch, so you can use git push in the future without specifying the branch name.

12. git push

- Push to Remote Repository

13. git ls-remote --heads origin

- Check Remote Repository. Double-check that the branch 'develop' actually exists in the remote repository. This command will list all the branches in the remote repository.

14. git pull origin master

- Pull Latest Changes. Ensure you have the latest updates from the remote repository by running this command. This fetches and merges the latest changes from the 'master' branch. After this, you might have a 'develop' branch if it was created in the remote repository after you cloned the repository.

15. git branch -d develop

- To delete a branch named 'develop' in Git, you can use the git branch command with the -d option. However, before you delete the branch, make sure that you're not currently on the branch you're trying to delete. If you're on the branch you want to delete, switch to a different branch first using the git checkout command.

16. git branch -D develop

- If you have unmerged changes on the 'develop' branch, Git will not allow you to delete it using the -d option. In that case, you can use the -D option to force delete the branch, even if it has unmerged changes.

17. git log

- This will display a list of commits in your repository along with their commit hashes. Each commit hash is a long string of characters, typically in the format of a 40-character hexadecimal number, like abcdef1234567890abcdef1234567890abcdef12.

18. git reset abcdef1234567890abcdef1234567890abcdef12

- This will reset your current branch to the commit identified by the hash abcdef1234567890abcdef1234567890abcdef12. Remember that when you reset to a specific commit, you're changing the branch's history, SO USE THESE COMMANDS WITH CAUTION.

- If you want to undo a specific commit and all subsequent commits, you can use these following. This will remove the specified commit and all commits after it. Use with caution as this can rewrite history and potentially lead to data loss.

19. git reset --soft HEAD~1

- Undoing a Commit and Keeping Changes. If you want to undo a commit but keep the changes from that commit as uncommitted changes in your working directory, you can use these command.

- Assume we have the following commit history: A - B - C (HEAD)
- A, B, and C are commit hashes.
- HEAD is pointing to commit C.
- Now, let's say you want to undo the most recent commit (C) but keep the changes from that commit as uncommitted changes in your working directory. You would use the following command: git reset --soft HEAD~1

- Here's what happens step by step:

1. Running the command tells Git to move the HEAD pointer and the branch reference (if applicable) to the commit one parent behind the current HEAD commit. In this case, it moves from commit C to commit B.

2. The changes introduced in commit C are "unstaged" and appear as uncommitted changes in your working directory. These changes are retained for you to review and potentially modify before making a new commit.

A - B (HEAD)
\
 C (Unstaged changes in working directory)

- You can now modify the files as needed and then create a new commit to incorporate the changes.

- Please remember that using git reset to modify commits and history should be done with caution, especially when working with shared repositories. It's a powerful tool that can rewrite history, so use it thoughtfully.

- you can use a partial commit hash (a few characters of the full hash) to refer to a specific commit in Git commands. Git will use the provided partial hash to match the most unique portion of the commit hash.

For example, if a full commit hash looks like abcdef1234567890abcdef1234567890abcdef12, you can use just the first few characters (e.g., abc or abcdef1) to uniquely identify that commit as long as the partial hash is unique within your repository's history.

Here's how you can use a partial commit hash in Git commands:

20. git reset --soft abc # Using partial hash "abc"

- Git will find the commit with a hash that starts with "abc" and use it for the operation.

- However, it's important to note that if multiple commits have the same starting characters in their hash, Git might not be able to uniquely identify the commit, and you might encounter an error. To avoid ambiguity, it's a good practice to use enough characters of the hash to make it unique within the context of your repository.

- Using a partial commit hash can be especially useful when you want to refer to a specific commit without needing to type or copy the entire hash. Just ensure that the partial hash you provide is unique enough to identify the intended commit accurately.

21. How to handle conflict when merge your code on branch

    A. Update Your Local Branch :

      Before merging your code, make sure your local branch is up to date with the latest changes from the target branch. You can do this by running:

        git checkout your-feature-branch

        git pull origin target-branch

    B. Start the Merge:
      
      Use the git merge or git pull command to merge the target branch into your feature branch. For example:

      git checkout your-feature-branch

      git merge target-branch

    C. Resolve Conflicts:

      If there are conflicts, Git will notify you and mark the conflicting areas in your code. You will need to open these files in your code editor and manually resolve the conflicts. Conflicts usually look something like this in your code:

        <<<<<<< HEAD
        // Your code
        =======
        // Code from the target branch
        >>>>>>>
    
    D. Test Your Changes:

      After resolving conflicts, test your code thoroughly to ensure that the changes you made, along with the resolved conflicts, work as expected.

    E. Add and Commit:

      Once the conflicts are resolved and you've tested your code, add the modified files and commit the changes:

        git add <conflicted-files>
        git commit -m "Merged changes from target-branch and resolved conflicts"

    F. Complete the Merge:

      Finish the merge by running:

        git merge --continue

    G. Push Your Changes:

      Finally, push your local changes to the remote repository:

        git push origin your-feature-branch

    H. Create a Pull Request (Optional):
      If you're using a pull request-based workflow (e.g., GitHub, GitLab), create a pull request from your feature branch to the target branch. This allows others to review your changes before merging them into the target branch.

      Remember that conflicts can sometimes be complex, and you may need to collaborate with team members to resolve them. Good communication and collaboration are key when dealing with conflicts in a team setting.

      Additionally, consider using a merge or rebase strategy that best fits your team's workflow. Merge and rebase have their own pros and cons, and the choice depends on your specific use case and preferences.

22. Step by step process how to Pull Request, Review, Approve and Merge

    Certainly, here's a step-by-step process for creating a Pull Request, reviewing, approving, and merging code in a typical Git-based workflow, using a platform like GitHub or GitLab:

    Step 1: Create a Pull Request

    1. Fork the Repository (if you don't have write access): If you don't have direct write access to the repository, fork it on the platform (e.g., GitHub). This creates your personal copy of the repository.

    2. Clone the Repository (Your Fork): Clone your forked repository to your local machine:

            git clone https://github.com/your-username/your-fork.git
    
    3. Create a New Branch: Create a new branch in your local repository where you'll make your changes.

            git checkout -b feature-branch

    4. Make Code Changes: Make your code changes on this feature branch.

    5. Commit and Push: Commit your changes and push them to your fork:

            git add .
            git commit -m "Description of changes"
            git push origin feature-branch
    
    6. Create a Pull Request: On the platform (e.g., GitHub), navigate to the original repository, switch to your feature branch, and click on the "New Pull Request" button. Follow the prompts to create the Pull Request.

    Step 2: Review the Pull Request

    Request Reviewers: Assign one or more team members as reviewers for your Pull Request. They will be notified to review your changes.

    Reviewers Review Code: Reviewers will examine your code changes, leave comments, and provide feedback through the platform's interface.

    Make Changes (if necessary): If reviewers request changes or make suggestions, make the necessary code adjustments, commit those changes, and push them to your branch.

    Step 3: Approve the Pull Request

    Reviewers Approve: Once reviewers are satisfied with your code, they can approve the Pull Request on the platform.

    Address Merge Conflicts (if any): If there are merge conflicts with the target branch, resolve them as described in the previous response. This is typically done in your local branch, then push the resolved changes to the Pull Request.

    Step 4: Merge the Pull Request

    Maintainer (Repo Owner or Admin) Merges: The maintainer of the repository (usually a project owner or an admin) will merge the Pull Request into the main branch.

    Pull Request is Closed: Once the Pull Request is merged, it is typically closed, and the changes are now part of the main branch.

    Cleanup: After merging, you can delete the feature branch both locally and on your fork (if applicable).

        # Locally
        git checkout main
        git branch -d feature-branch

        # On your fork
        git push origin --delete feature-branch

    Keep in mind that the exact process can vary depending on the platform you're using and the specific workflow of your team or project. This general process is commonly used in many open-source and collaborative development environments.