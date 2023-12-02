# Assignment

Before you start!

- Github recently updated the way it names the default branch. This means you need to make sure you are using a recent version of git (2.28 or later). You can check your version by running: `git --version`
- If you haven’t already, set your local default git branch to `main`. You can do so by running: `git config --global init.defaultBranch main`
- For more information on the change from `master` to `main` see GitHub’s Renaming Repository.

## Create the repository

1. You should have already created a GitHub account in the Setting Up Git lesson. If you haven’t done that yet, you can sign up here.
2. Create a new repository by clicking the button shown in the screenshot below.
3. Give your repository the name “git_test” in the repository name input field. Check “Add a README file”. And then create the repository by clicking the “Create repository” button at the bottom of the page.
4. This will redirect you to your new repository on GitHub. To get ready to copy (clone) this repository onto your local machine, click the green “Code” button. Then select the SSH option, and copy the line below it. **NOTE: You MUST click the SSH option to get the correct URL.**
5. Let’s use the command line on your local machine to create a new directory for all of your Odin projects. Create a directory called `repos` with the `mkdir` command in your home folder. Your home folder is represented by `~`. Navigating Files and Directories covered variations of home folders - sometimes `~` stands for `/Users/your_username` and sometimes it stands for `/home/your_username`. If you’re not sure if you’re in your home folder, just type `cd ~`. Once it’s made, move into it with the `cd` command.
6. Now it’s time to clone your repository from GitHub onto your computer with `git clone` followed by the URL you copied in the last step. The full command should look similar to `git clone git@github.com:USER-NAME/REPOSITORY-NAME.git`. If your URL looks like `https://github.com/USER-NAME/REPOSITORY-NAME.git`, you have selected the HTTPS option, not the required SSH option.
7. That’s it! You have successfully connected the repository you created on GitHub to your local machine. To test this, you can `cd` into the new **git_test** folder that was downloaded and then enter `git remote -v` on your command line. This will display the URL of the repository you created on GitHub, which is the remote for your local copy. You may have also noticed the word **origin** at the start of the `git remote -v` output, which is the name of your remote connection. The name “origin” is both the default and the convention for the remote repository. But it could have just as easily been named “party-parrot” or “dancing-banana”. (Don’t worry about the details of origin for now; it will come up again near the end of this tutorial.)

## Use the Git workflow

1. Create a new file in the `git_test` folder called “hello_world.txt” with the command `touch hello_world.txt`.
2. Type `git status` in your terminal. In the output, notice that your `hello_world.txt` file is shown in red, which means that this file is not staged.
3. Type `git add hello_world.txt`. This command adds your hello_world.txt file to the staging area in Git. The staging area is part of the two-step process for making a commit in Git. Think of the staging area as a “waiting room” for your changes until you commit them. Now, type git status again. In the output, notice that your file is now shown in green, which means that this file is now in the staging area.
4. Type git commit -m "Add hello_world.txt" and then type git status once more. The output should now say: “nothing to commit, working tree clean”, indicating your changes have been committed. Don’t worry if you get a message that says “upstream is gone”. This is normal and only shows when your cloned repository currently has no branches. It will be resolved once you have followed the rest of the steps in this project.

The message, “Your branch is ahead of ‘origin/main’ by 1 commit” just means that you now have newer snapshots than what is on your remote repository. You will be uploading your snapshots further down in this lesson.

5. Type git log and look at the output. You should see an entry for your “Add hello_world.txt” commit. You will also see details on the author who made the commit and the date and time of when the commit was made. If your terminal is stuck in a screen with (END) at the bottom, just press “q” to escape. You can configure settings for this later, but don’t worry about it too much for now.

## Modify a file or two

1. Open README.md in your text editor of choice. In this example, we will open the directory in Visual Studio Code by using the command code . inside your repository.

MacOS users: If your terminal reads “command not found: code”, you must head back to Command Line Basics and follow the instructions provided to allow this command to work.

2. Add “Hello Odin!” to line 3 of README.md and save the file with Ctrl + S (Mac: Cmd + S).

1. Go back to your terminal or if you’re using Visual Studio Code you can open the built-in terminal by pressing Ctrl + ` (backtick). Then type git status. You’ll notice that README.md is now shown as not staged or committed.
2. Add README.md to the staging area with git add README.md.
3. Can you guess what git status will output now? README.md will be displayed in green text. That means README.md has been added to the staging area. The file hello_world.txt will not show up because it has not been modified since it was committed.
4. Open `hello_world.txt`, add some text to it, save it and stage it. You can use git add . to add all files in the current directory and all subsequent directories to the staging area. Then, type git status once more, and everything should now be in the staging area.
5. Finally, let’s commit all of the files that are in the staging area and add a descriptive commit message. git commit -m "Edit README.md and hello_world.txt". Then, type git status once again, which will output “nothing to commit”.
6. Take one last look at your commit history by typing git log. You should now see three entries.

## Push your work to GitHub

Finally, let’s upload your work to the GitHub repository you created at the start of this tutorial.

1. Type git push. To be more specific, type git push origin main. Since you are not dealing with another branch (other than main) or a different remote (as mentioned above), you can leave it as git push to save a few keystrokes. **NOTE: If at this point you receive a message that says “Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.”, you have followed the steps incorrectly and cloned with HTTPS, not SSH. Please follow these steps to change your remote to SSH, then attempt to push to Github.**
2. Type git status one final time. It should output “Your branch is up to date with ‘origin/main’. nothing to commit, working tree clean”.
3. When you reload the repository on GitHub, you should see the README.md and hello_world.txt files that you just pushed there from your local machine.