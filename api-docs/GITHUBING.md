# GitHub workflow :octocat:

To contribute content to this repository (repo), use the GitHub workflow described here. 
To follow the entire contribution process, go to 
[CONTRIBUTING.md](CONTRIBUTING.md).

**Note:** This workflow shows how to make changes to the repo from the command line by 
using git commands. If you do not want to use the command line, you can use GitHub Desktop 
or another GitHub GUI instead to accomplish the steps. 
  

## Prerequisite

* [Generate SSH keys](https://help.github.com/articles/generating-ssh-keys/)

## Workflow

### Fork, clone, and track the upstream the repository

1. Create a fork of this repo.

2. Use the ssh URL for the forked repo to clone it to your local system.

    ```bash

    git clone git@github.com:my-github-username/docs-cloud-identity.git

    ```

3. Track the upstream repo
    
    ```bash
    cd getcarina.com
    git remote add --track master upstream git@github.com:rackerlabs/docs-cloud-identity.git
    ````
    
### Update or add new content 


#### Synch your copy of the repo and create a branch

Collaborating on GitHub means that the main repository can be updated by many people. 
Synching with the master helps prevent merge conflicts caused by multiple people 
making conflicting changes to the same content. 

Creating a branch allows you to group a set of updates for a specific feature or 
development milestone in a copy of the repo without changing the production content in the 
master branch. Then, you can submit changes to the master branch when you want them to 
be published.  

Complete the following steps to synch your repository and create a branch for changes: 


1.  Bring your repo up-to-date with the upstream repo
   
    ```bash
    git checkout master
    git pull --rebase upstream master
    ```

1. Create a branch for changes. For details about this part of the workflow, see 
   [Understanding the GitHub Flow](https://guides.github.com/introduction/flow/index.html) 
   guide.
    
    ```
    bash
    git checkout -b <name-of-branch>
    ```
    
**Tips:** 
   - To view the branches on the repository, type ``git branch``.
   - To switch between branches, type ``git checkout <branchname>``
   - The branch you are on is indicated by an asterisk (*).  
   
#### Step 1: Update or add content 

1. Before making any changes, synch your repo with the upstream version.

    ```
        git fetch upstream
        git rebase upstream/master
    ```
    
    If any updates are added, push them to your GitHub fork:
    
    ```
      git push
    ```

1. Checkout or create a branch, make changes to existing files and add new files, as needed. 
   ```bash
    git add .
    ```
    
1. Add all files relevant to the change 
   
   ```
   git add .
   ```

1. Commit the changed files.
    ```bash
    git commit -m "The reason for my change"
    ```

1. Push your local branch to your fork
    ```bash
    git push -u origin <name-of-branch>
    ```

#### Step 2: Submit your changes for review

1. Create a pull request (PR) to the upstream repo for your branch

    a. Go to https://github.com/rackerlabs/docs-cloud-identity
    b. Click on the Create pull request button
    c. If this PR is related to an outstanding github 
      [GitHub issue](https://github.com/rackerlabs/docs-cloud-identity/issues), include a link to that GitHub issue in the comment

1. Notify your technical reviewers that the PR is ready for 
    [technical review](CONTRIBUTING.md#technical-review).

1. If necessary, incorporate changes from the review, make updates to your PR by adding 
    more commits.
    
    ```bash
    git add .
    git commit -m "The reason for my update"
    git push -u origin <name-of-branch>
    ```

1. When the tech review is complete, notify your editor that the PR is ready for an 
    editorial review.
    
    
1. Repeat steps to add and commit any additional changes requested by reviewers as needed. 

1. Resolve conflicts, if necessary.

    During your review process, someone might have already updated and merged a file that 
    you are in the process of changing. . Such a conflict means that you can’t merge your 
    PR. To resolve the conflict, perform the following steps. 
    
    a. Bring your branch up-to-date with the upstream repo by running the following 
       commands from your branch:
       
       ```
        git fetch upstream
        git rebase upstream/master
       ```
    
    b. Follow the steps to [resolve a merge conflict from the command line](https://help.github.com/articles/resolving-a-merge-conflict-from-the-command-line/).

1. When the editorial review, any conflicts are resolved, and the merge button is green,
    [merge the PR](CONTRIBUTING.md#merge-it).

#### Step 3: Update your copies of the production content

Type the following commands to merge the latest updates to your local copy of the repository and push them to your fork.

    ```bash
    git checkout master
    git pull --rebase upstream master
    git push
    ```

### Git Tips

To see repository status in your prompt and to activate auto-completion, 
perform the following steps:

1. Download 
[git-prompt.sh](https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh) 
and save it in your home directory as .git-prompt.sh
   
1. Download 
[git-completion.bash](https://github.com/git/git/blob/master/contrib/completion/git-completion.bash) 
and save it in your home directory as .git-completion.bash

1. Add the following to your .bash_profile in your home directory

```bash
GIT_PS1_SHOWDIRTYSTATE=1
GIT_PS1_SHOWUNTRACKEDFILES=1
GIT_PS1_SHOWCOLORHINTS=1
GIT_PS1_SHOWUPSTREAM=1
source ~/.git-prompt.sh
source ~/.git-completion.bash
```

## Help

* [Understanding the GitHub Flow](https://guides.github.com/introduction/flow/index.html)
* [Mastering GitHub Issues](https://guides.github.com/features/issues/)
* [GitHub Help](https://help.github.com/)
