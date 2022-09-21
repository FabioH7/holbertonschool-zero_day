
# Git and Github

## What is Git

     Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency . To learn more about Git click [here](https://git-scm.com/)
     
## How to set up git in your sandbox

>- The first thing you should after you install git is to set up you credentials(username and email):

```shell
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```
>- Then you should check out if your Github credentials are set using this:
```shell
$ git config --list --show-origin
```

>- Then you should set up your ssh key by using this command and substituting in your github email:

```shell
$ ssh-keygen -t ed25519 -C "your_email@example.com"
```

>When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location. And at the prompt, type a secure passphrase.

## How to create a repository

>- Using the graphic interface on the [Github](https://github.com/) website.
[Repostitory creation](https://www.google.com/url?sa=i&url=https%3A%2F%2Fcooc-china.gitbooks.io%2Fcooc-howto-book%2Fenglish-version%2Fcreate-the-book-and-make-connection-with-github-repository.html&psig=AOvVaw3gDZie24JoAbJrWZoqD4Za&ust=1663849720214000&source=images&cd=vfe&ved=0CAwQjRxqFwoTCMim7bPxpfoCFQAAAAAdAAAAABAP)
[PAT creation](https://raw.githubusercontent.com/devgemmy/gist-images/main/git-token.png)
>- Then you need to clone your repository
```shell
root@896cf839cf9a:/# git clone https://{YOUR_PERSONAL_TOKEN}@github.com/{YOUR_USERNAME}/{YOUR_REPO}.git                  
Cloning into '{YOUR_REPO}'...
warning: You appear to have cloned an empty repository.
```
>- All you need to do now is to navigate to the repository, create the README.md and push the modifications
```shell
root@896cf839cf9a:/# cd {YOUR_REPO}/
root@896cf839cf9a:/{YOUR_REPO}#
```
```shell
root@896cf839cf9a:/{YOUR_REPO}# echo 'My first readme' > README.md                                                                 
root@896cf839cf9a:/{YOUR_REPO}# cat README.md                                                                                      
My first readme 
```
```shell
root@896cf839cf9a:/{YOUR_REPO}# git add .
root@896cf839cf9a:/{YOUR_REPO}# git commit -m 'My first commit'
[master (root-commit) 98eef93] My first commit
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
root@896cf839cf9a:/{YOUR_REPO}# git push                                                                                           
Enumerating objects: 3, done.                                                                                                         
Counting objects: 100% (3/3), done.                                                                                                   
Writing objects: 100% (3/3), 212 bytes | 212.00 KiB/s, done.                                                                          
Total 3 (delta 0), reused 0 (delta 0)                                                                                                 
To https://github.com/{YOUR_USERNAME}/{YOUR_REPO}.git                                                                                       
 * [new branch]      master -> master 
```
 
>- Before continuing you need to familiarize yourself with some useful git commands
- Basic commands needed
```
git add file_name
git add .
```
The git add command adds a change in the working directory to the staging area. It tells Git that you want to include updates to a particular file in the next commit
```
git commit -m "Meaningful message"
```
Create a new commit containing the current contents of the index and the given log message describing the changes
```
git push
```
The git push command is used to upload *local* repository content to a *remote* repository. Pushing is how you transfer commits from your local repository to a remote repo.
```
git pull
```
The git pull command is used to fetch and download content from a remote repository and immediately update the local repository to match that content. Merging remote upstream changes into your local repository is a common task in Git-based collaboration work flows.
### Branching and merging
- Understanding branching
Branching in Git is used as a form of creating an identical copy of the current files and materials currently stored in your repository. Let's take a simple example that Team A and Team B need to update different files on the same *main* branch. In order to avoid conflict and confusion both of these teams would create new branches(branch a and branch b) so they can update and test their code without changing anything in the source material.
- Understanding merging
Merging basically merges the updated files of different branches to other branches. In the above example, suppose that Team A and Team B have updated and successfully tested their code and are ready to update the final 'main' branch. They would merge their individual branches with the main branch, thus updating the final product.
- Merging conflicts
Merge conflicts occur when competing changes are made to the same line of a file, or when one person edits a file and another person deletes the same file.
To resolve a merge conflict caused by competing line changes, you must choose which changes to incorporate from the different branches in a new commit.
For example, if you and another person both edited the file **styleguide.md** on the same lines in different branches of the same Git repository, you'll get a merge conflict error when you try to merge these branches. You must resolve this merge conflict with a new commit before you can merge these branches.
- Resolving merge conflicts using the terminal
1) In the terminal, ```cd``` into the repository that has the conflict
2) Generate a list of the files affected by the merge conflict. In this example, the file **styleguide.md** has a merge conflict.
```
$ git status
> # On branch branch-b
> # You have unmerged paths.
> #   (fix conflicts and run "git commit")
> #
> # Unmerged paths:
> #   (use "git add ..." to mark resolution)
> #
> # both modified:      styleguide.md
> #
> no changes added to commit (use "git add" and/or "git commit -a")
```
3) Open a text editor of your choice and navigate to the conflicted file
4) To see the beginning of the merge conflict in your file, search the file for the conflict marker ```<<<<<<<```. When you open the file in your text editor, you'll see the changes from the HEAD or base branch after the line ```<<<<<<< HEAD```. Next, you'll see ```=======```, which divides your changes from the changes in the other branch, followed by ```>>>>>>> BRANCH-NAME```.
5) Decide if you want to keep only your branch's changes, keep only the other branch's changes, or make a brand new change, which may incorporate changes from both branches. Delete the conflict markers ```<<<<<<<```, ```=======```, ```>>>>>>>``` and make the changes you want in the final merge. In this example, both changes are incorporated into the final merge.
6) Add , commit and push changes.
