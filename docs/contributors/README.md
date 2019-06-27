# Project Roadmap
Check the [roadmap file](./roadmap.md) for now as initial development of the MVP is being discussed.

# Contributor Workflow
1. Perform an initial, one-time, fork of the main repository on GitHub.

2. Perform an initial, one-time, git clone onto your local machine in the directory you want to keep the project.

    ```
    git clone git@github.com:you/project-bueller.git
    ```

3. Initial, one-time, git add of remote upstream repository:
    ```
    git remote add upstream git://github.com/rgroves/project-bueller.git
    ```

4. Create a branch for your changes. Name the branch by issue number and description. Develop on this issue branch. Be sure to commit and rebase periodically*. If there is not an existing issue for the change you want to make create a new issue in the upstream repo on GitHub for review before working on it.
    ```
    git branch ###-description
    git checkout ###-description
    ```
    *...make some changes in your issue branch, then commit those changes...*
    ```
    git commit -am "Description of changes."
    ```
    **Rebasing your work periodically:*

    As time passes, the upstream project repository will accumulate new commits. Keep your working copy up-to-date by periodically rebasing your working copy's master branch and issue branch(es) on upstream's master branch.
    ```
    git checkout master
    git fetch upstream
    git rebase upstream/master
    git checkout ###-description
    git rebase master
    ```

5. When you're finished working on an issue, rebase one last time, then create a new release candidate branch based on the issue branch.
    ```
    git checkout ###-description
    git branch ###-description-rc
    git checkout ###-description-rc
    ```
    Squash all *X* commits that pertain to this issue into one clean, descriptive commit.
    ```
    git rebase -i HEAD~X
    ```

6. Push the release candidate branch to origin.
    ```
    git push origin ###-description-rc
    ```

7. Send a Pull Request to the upstream repo on GitHub.