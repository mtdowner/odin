### Assignment

<div class="lesson-content__panel" markdown="1">

#### Before you start!

-   Github recently updated the way it names the default branch. This means you need to make sure you are using a recent version of git (2.28 or later). You can check your version by running:
  `git --version`
-   If you haven't already, set your <span id="main-push"></span>local default git branch to `main`. You can do so by running:
  `git config --global init.defaultBranch main`
-   For more information on the change from `master` to `main` see [GitHub's Renaming Repository](https://github.com/github/renaming).

#### Create the repository

1.  <span id="new-github-repo"></span>You should have already created a GitHub account in the [Setting Up Git](https://www.theodinproject.com/lessons/foundations-setting-up-git) lesson. If you haven't done that yet, you can sign up [here](https://github.com/).

2.  Create a new repository by clicking the button shown in the screenshot below.

    ![The GitHub Profile Screen](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/00.png)

3.  Give your repository the name "git_test" in the repository name input field. Check "Add a README file". And then create the repository by clicking the "Create repository" button at the bottom of the page.

    ![Create new repo using GitHub](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/01.png)

4.  This will redirect you to your new repository on GitHub. To get ready to copy (clone) this repository onto your local machine, click the green "Code" button. Then select the SSH option, and copy the line below it. **NOTE: You MUST click the SSH option to get the correct URL.**

    ![Copy SSH link using GitHub](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/02.png)

5.  Let's use the command line on your local machine to create a new directory for all of your Odin projects. Create a directory called `repos` with the `mkdir` command in your home folder. Your home folder is represented by `~`. [Navigating Files and Directories](https://swcarpentry.github.io/shell-novice/02-filedir.html#callout1) covered variations of home folders - sometimes `~` stands for `/Users/your_username` and sometimes it stands for `/home/your_username`. If you're not sure if you're in your home folder, just type `cd ~`. Once it's made, move into it with the `cd` command.

    ![Creating a new directory](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/03.png)

6.  <span id="github-to-local"></span>Now it's time to clone your repository from GitHub onto your computer with `git clone` followed by the URL you copied in the last step. The full command should look similar to `git clone git@github.com:USER-NAME/REPOSITORY-NAME.git`. If your URL looks like `https://github.com/USER-NAME/REPOSITORY-NAME.git`, you have selected the HTTPS option, not the required SSH option.

    ![Clone the repo using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/04.png)

7.  <span id="origin-push"></span>That's it! You have successfully connected the repository you created on GitHub to your local machine. To test this, you can `cd` into the new **git_test** folder that was downloaded and then enter `git remote -v` on your command line. This will display the URL of the repository you created on GitHub, which is the remote for your local copy. <span id="default-remote"></span>You may have also noticed the word **origin** at the start of the `git remote -v` output, which is the name of your remote connection. The name "origin" is both the default and the convention for the remote repository. But it could have just as easily been named "party-parrot" or "dancing-banana". (Don't worry about the details of origin for now; it will come up again near the end of this tutorial.)

    ![Check repo remotes using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/05.png)

#### Use the Git workflow

1.  Create a new file in the `git_test` folder called "hello_world.txt" with the command `touch hello_world.txt`.

    ![Create hello_world.txt using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/06.png)

2.  <span id="git-status"></span>Type `git status` in your terminal. In the output, notice that your hello_world.txt file is shown in red, which means that this file is not staged.

    ![Check status of repo using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/07.png)

3.  <span id="git-add"></span><span id="two-stages"></span>Type `git add hello_world.txt`. This command adds your hello_world.txt file to the staging area in Git. The staging area is part of the two-step process for making a commit in Git. Think of the staging area as a "waiting room" for your changes until you commit them. Now, type `git status` again. In the output, notice that your file is now shown in green, which means that this file is now in the staging area.

    ![Stage hello_world and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/08.png)

4.  <span id="git-commit"></span>Type `git commit -m "Add hello_world.txt"` and then type `git status` once more. The output should now say: "*nothing to commit, working tree clean*", indicating your changes have been committed. Don't worry if you get a message that says "*upstream is gone*". This is normal and only shows when your cloned repository currently has no branches. It will be resolved once you have followed the rest of the steps in this project.

    The message, "_Your branch is ahead of 'origin/main' by 1 commit_" just means that you now have newer snapshots than what is on your remote repository. You will be uploading your snapshots further down in this lesson.

    ![Commit hello_world and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/09.png)

5.  <span id="git-log"></span>Type `git log` and look at the output. You should see an entry for your "*Add hello_world.txt*" commit. You will also see details on the author who made the commit and the date and time of when the commit was made. If your terminal is stuck in a screen with (END) at the bottom, just press "q" to escape. You can configure settings for this later, but don't worry about it too much for now.

    ![Commit hello_world and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/10.png)

#### Modify a file or two

1.  Open README.md in your text editor of choice. In this example, we will open the directory in Visual Studio Code by using the command `code .` inside your repository.

    ![Add text file and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/11.png)

    MacOS users: If your terminal reads *"command not found: code"*, you must head back to [Command Line Basics](https://www.theodinproject.com/lessons/foundations-command-line-basics#opening-files-in-vscode-from-the-command-line) and follow the instructions provided to allow this command to work.

2.  Add "Hello Odin!" to line 3 of README.md and save the file with <kbd>Ctrl</kbd> + <kbd>S</kbd> (Mac: <kbd>Cmd</kbd> + <kbd>S</kbd>).

    ![Edit README using text editor](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/12.png)

<!-- code element needed to not treat the backtick inside the kbd element as code markdown -->
3.  Go back to your terminal or if you're using Visual Studio Code you can open the built-in terminal by pressing <kbd>Ctrl</kbd> + <kbd>`</kbd> (backtick). Then type <code>git status</code>. You'll notice that README.md is now shown as not staged or committed.

    ![Check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/13.png)

4.  Add README.md to the staging area with `git add README.md`.

5.  Can you guess what `git status` will output now? README.md will be displayed in green text. That means README.md has been added to the staging area. The file hello_world.txt will not show up because it has not been modified since it was committed.

    ![Stage README changes and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/14.png)

6.  Open hello_world.txt, add some text to it, save it and stage it. You can use `git add .` to add all files in the current directory and all subsequent directories to the staging area. Then, type `git status` once more, and everything should now be in the staging area.

    ![Stage all other files in repo and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/15.png)

7.  Finally, let's commit all of the files that are in the staging area and add a descriptive commit message. `git commit -m "Edit README.md and hello_world.txt"`. Then, type `git status` once again, which will output "*nothing to commit*".

    ![Commit repo changes again and check repo status again using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/16.png)

8.  Take one last look at your commit history by typing `git log`. You should now see three entries.

    ![Git Log](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/17.png)

#### Push your work to GitHub

Finally, let's upload your work to the GitHub repository you created at the start of this tutorial.

1.  <span id="git-push"></span>Type `git push`. To be more specific, type `git push origin main`. Since you are not dealing with another branch (other than _main_) or a different remote (as mentioned above), you can leave it as `git push` to save a few keystrokes. **NOTE: If at this point you receive a message that says "Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.", you have followed the steps incorrectly and cloned with HTTPS, not SSH. Please follow [these steps](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories#switching-remote-urls-from-https-to-ssh) to change your remote to SSH, then attempt to push to Github.**

    ![Push changes to remote using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/18.png)

2.  Type `git status` one final time. It should output "_Your branch is up to date with 'origin/main'. nothing to commit, working tree clean_".

    ![Check repo status again to confirm local repo is up to date with remote using CLI](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/19.png)

3.  When you reload the repository on GitHub, you should see the README.md and hello_world.txt files that you just pushed there from your local machine.

     ![Verify repo changes are on GitHub](https://cdn.statically.io/gh/TheOdinProject/curriculum/b54d14c5dcee1c6fac61aee02fca7e9ef7ba1510/foundations/git_basics/project_practicing_git_basics/imgs/20.png)

</div>