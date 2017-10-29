## GIT basic usage / submitting tasks
#### Web-sovelluskehityksen perusteet 
#### Ilkka Kylmäniemi

##### What you need:
* Windows
    * [Git for windows (Git Bash)](https://git-for-windows.github.io/)
* OS X
    * press cmd-space and type terminal

#### When starting a new task from scratch:
1. Open terminal or Git Bash
2. Go to desired folder e.g. `Documents/tasks
    ```
    cd ~/Documents/tasks
3. Create a new folder for the task
    ```
    mkdir taskName
4. Go into the task folder
    ```
    cd taskName
5. Create a new repo in GitHub and copy/paste the commands under '…or create a new repository on the command line'. It looks something like this:
    ```
    echo "# nameOfTheRepo" >> README.md
    git init
    git add README.md
    git commit -m "first commit"
    git remote add origin https://github.com/username/nameOfTheRepo.git
    git push -u origin master
6. Now you can start doing the task
    * You should edit the README.md to add the name of the task and some description.
7. When you want to push new version to GitHub (for example when the task is eady)
    ```
    git add .
    git commit -m 'message'
    git push
8. You can view the repo at `https://github.com/username/nameOfTheRepo`

#### When starting a new task by cloning a repo:
1. Open terminal or Git Bash
2. Go to desired folder e.g. `Documents/tasks
    ```
    cd ~/Documents/tasks
3. Clone the task's repo
    ```
    git clone urlToRepo
4. After cloning you have a folder with the same name as the repo
    ```
    cd repoName
5. Now you can start doing the task
    * Do what ever is required by the task
    * Edit the README.md as appropriate
6. When you want to push new version to GitHub (for example when the task is ready), you need to set a new location:
    * Create a new repo in GitHub and run these commands (of course edit the urls): 
    ```
    git remote set-url origin https://github.com/username/nameOfTheRepo.git
    git add .
    git commit -m 'message'
    git push -u origin master
7. You can view the repo at `https://github.com/username/nameOfTheRepo`
