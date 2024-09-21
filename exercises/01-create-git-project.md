# Create your first Git project

In this exercise, we will use the Git command-line interface to establish a new project tracked in Git, and commit our first change to the repository.

We're going to use the Git Bash shell tool, which supports UNIX-style commands. Git Bash is installed as part of the Git client you downloaded from [git-scm.com](https://git-scm.com).

1. On your local disk, open up a Git Bash shell and navigate to the root folder where you want to work. Then, create a new directory and change (cd) into it. (This will be the directory we work in unless otherwise specified). An example is shown below.
   ```
   mkdir sesug
   cd sesug
   ```

   Verify that the current folder is **not** tracked by Git by running the **git status** command.
    ```
    git status
    ```
 
2. In the new directory, create a new SAS program file by using the **echo** command or by copying an existing SAS program to the folder.
   ```
   echo "proc options; run;" > sas-git.sas
   ```

3. Initialize a new repo by using the **git init** command.
   ```
   git init --initial-branch=main
   ```

   This command creats a new git repository skeleton in a subdirectory named ".git" under the current directory - as indicated by the output message from the command. This means that you’re now able to start using other Git commands in the current directory.

4. Check to see if Git "knows who you are" in the configuration. Git config values are sometimes set as you install tools, or by you explicitly as you issue commands. This command checks whether you set your name and email:
   ```
   git config --list --show-origin | grep user
   ```

5. If needed, tell Git who you are by setting your basic identification configuration settings with the following commands (Note the double dashes before “global” since we are spelling out the option. Also, values only require quotes if there is a space in the value.)
   ```
   git config --global user.name "First-name Last-name"
   git config --global user.email emailAddress@provider
   ```

6. Stage your project files with the **git add** command. The dot ('.') tells Git to add all available files, including those in subfolders.
   ```
   git add .
   ```
   For fun, check the repo status again:
   ```
   git status
   ```

7. Now commit the files. You can use whatever commit message (comment) you want.
   ```
   git commit -m "initial commit"
   ```

   Notice the output you get. There is the branch name (the default branch is **main**), followed by an indicator that this was the first (root) commit and then the first few characters of the SHA1 for the commit.

8. Edit one of the files. (We can just use the ">>" to append something to the file's content.)
   ```
   echo "/* Adding just a comment to my code */" >> sas-git.sas

9. Stage and commit the file with this shortcut (-am means stage all and commit instead of two operations).
   ```
   git commit -am "Added a comment"
   ```

10. Check repo history using the **git log** command.
    ```
    git log --pretty=format:"%h %ae %s"
    ```
    The **pretty** option specifiers can make a more concise, readable history log with certain fields. Or use the **--oneline** option for a quick view:
    ```
    git log --oneline
    ```
