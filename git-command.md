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

~~Using GitHub CLI on Windows OS~~

[GitHub CLI](https://github.com/cli/cli)

1. winget install --id GitHub.cli

- if GitHub CLI not install yet on your Windows OS

2. export PATH="$PATH:/C:\Program Files\GitHub CLI"

- add to path of bash (run on bash command)

3. create classic token API on your GitHub account at [Settings](https://github.com/settings/tokens)

- copy paste and save your token API (30 days expiration)

4. gh auth login

- access using SSH and token

5. gh auth logout

- logout from remote repository

6. gh repo create repository-name (create new repository on GitHub)

- You can also provide additional options like --public or --private to specify the repository's visibility, and --description to set a description.

7. git remote add origin git@github.com:username/repository-name.git

- add remote to your active repository

8. git branch

- Check Existing Branches

9. git fetch origin

- Fetch Branches from Remote Repository

10. git checkout -b new-branch-name

- a single command that combines branch creation and switching to the new created branch using the -b flag

- Remember that creating a new branch allows you to work on a new feature or bug fix without affecting the main development line. You can make changes, commit them to the new branch, and then merge the branch back into the main branch (e.g., master or develop) when the changes are ready.

11. git branch -M develop

- The command git branch -M develop is used to rename the current branch to develop. This command is often used when you want to change the name of the current branch, typically when you are working with the default branch of a Git repository and you want to rename it. The -M flag stands for "move" and indicates that you want to move or rename the branch. The develop argument specifies the new name you want to give to the branch.

12. git push -u origin develop

- Push to Remote Repository, Push your local commits to the remote repository on the main (or master or develop) branch (replace main with the appropriate branch name if needed). The -u flag sets the upstream branch, so you can use git push in the future without specifying the branch name.

13. git push

- Push to Remote Repository

14. git ls-remote --heads origin

- Check Remote Repository. Double-check that the branch 'develop' actually exists in the remote repository. This command will list all the branches in the remote repository.

15. git pull origin master

- Pull Latest Changes. Ensure you have the latest updates from the remote repository by running this command. This fetches and merges the latest changes from the 'master' branch. After this, you might have a 'develop' branch if it was created in the remote repository after you cloned the repository.

16. git branch -d develop

- To delete a branch named 'develop' in Git, you can use the git branch command with the -d option. However, before you delete the branch, make sure that you're not currently on the branch you're trying to delete. If you're on the branch you want to delete, switch to a different branch first using the git checkout command.

17. git branch -D develop

- If you have unmerged changes on the 'develop' branch, Git will not allow you to delete it using the -d option. In that case, you can use the -D option to force delete the branch, even if it has unmerged changes.

18. git log

- This will display a list of commits in your repository along with their commit hashes. Each commit hash is a long string of characters, typically in the format of a 40-character hexadecimal number, like abcdef1234567890abcdef1234567890abcdef12.

19. git reset abcdef1234567890abcdef1234567890abcdef12

- This will reset your current branch to the commit identified by the hash abcdef1234567890abcdef1234567890abcdef12. Remember that when you reset to a specific commit, you're changing the branch's history, SO USE THESE COMMANDS WITH CAUTION.

- If you want to undo a specific commit and all subsequent commits, you can use these following. This will remove the specified commit and all commits after it. Use with caution as this can rewrite history and potentially lead to data loss.

20. git reset --soft HEAD~1

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

21. git reset --soft abc # Using partial hash "abc"

- Git will find the commit with a hash that starts with "abc" and use it for the operation.

- However, it's important to note that if multiple commits have the same starting characters in their hash, Git might not be able to uniquely identify the commit, and you might encounter an error. To avoid ambiguity, it's a good practice to use enough characters of the hash to make it unique within the context of your repository.

- Using a partial commit hash can be especially useful when you want to refer to a specific commit without needing to type or copy the entire hash. Just ensure that the partial hash you provide is unique enough to identify the intended commit accurately.
