---
layout: post
title:  "Git, A Fast Guide for Newcomers."
date:   2017-05-07 00:20:12 -0500

tags:
  - Git
  - Github
  - Ubuntu
  - Linux

categories:
  - Version_System_Manager
---

This is a guide for novice on use git tool to practice with a version control system.

# git

Git is a software control version system, using logs, you can see all modification (named as commit) of one project.

    sudo apt-get install git

First of all, set your user info in your host machine.

* For one local repository, on the actual dir:

      git config user.name "username"
      git config user.email "usermail"

* For all repositories on our machine:

      git config --global user.name "username"
      git config --global user.email "usermail"

## Creating a new repository

There are 2 methods:

* First of them, using [github](https://github.com).

  * In github homepage, with your user logged, click on the `+` button located on left-top of screen.

    ![new_repo_github][new-repo]

  * Then, choose a repository name y add some description and press Create repository.
  
    ![descrip_repo_github][descrip-repo]

    If you choose `Initialize this repository with a README` automatically creates a repository.

  * Then, github shows this screen, with 4 options:
  
    ![option_repo_github][option-repo]

    * Create a README, LICENSE and .gitignore files:
    
      If you click on any of that options, github shows this screen (I choose README).
      
      ![readme_repo_github][readme-repo]
    
      Then click on `commit new file`, and now you created your first repository.
      
      ![created-repo_github][created-repo]
    
    * Create a new repository on the command line:
    
      Create a dir to test git commands:
      
          mkdir gitTest
          cd gitTest
        
        ![created-repo_CLI][created-repoCLI]
    
      Then, check on your reposiory example and see the changes.
      
      ![created-repo_github][created-repo]
    
    * Import code from another repo, Write the remote repository url:
    
      ![import-repo_github][import_repo]
      
      Click on `Begin import` and wait a few minutes while is copying the remote repo.
      
      ![imported-repo_github][imported_repo]
      
      Or click on `change repository`, this will be clone a remote repository to a new repository (different of example).

      ![import-new-repo_github][import_newrepo]
      
      Then, check your example repository and see files that were cloned.
      
      ![cloned-imported_github][conedImported-repo]
  
  
* Second, create a repository from terminal:
  
      repo_name="example"
      github_username="Jenazad"
      curl -u $github_username https://api.github.com/user/repos -d "{\"name\":\"$repo_name\"}"

    * Next, we init the local repository:
    
          git init
          git remote add origin "https://github.com/$github_username/$repo_name.git"
    
    * And then, create some file like `Readme.md` and push it:
  
          touch Readme.md
          git add .
          git commit -m "readme"
          git push origin master
      
## Commands

* Check file status:
  
      git status

* Add files/directories to the local repository:

      git add .

* Confirms the uploaded files and set ready to upload to remote from local repository:

      git commit -m "modify"

* Push new files to remote repository:

      git push origin master

* Pull newest uploaded files from remote to local repository:

      git pull origin master

* Configurate a local repository in `.git/config` add the fields

	    [remote "origin"]
		    url = https://github.com/path/repo.git
		    fetch = +refs/heads/*:refs/remotes/origin/*


[new-repo]:            /assets/systemVersionSoftware/Git/repo_new_github.png
[descrip-repo]:        /assets/systemVersionSoftware/Git/repo_descrip_github.png
[option-repo]:         /assets/systemVersionSoftware/Git/repo_option_github.png
[readme-repo]:         /assets/systemVersionSoftware/Git/repo_readme_github.png
[created-repo]:        /assets/systemVersionSoftware/Git/repo_created_github.png
[import_repo]:         /assets/systemVersionSoftware/Git/repo_import_github.png
[imported_repo]:       /assets/systemVersionSoftware/Git/repo_imported_github.png
[import_newrepo]:      /assets/systemVersionSoftware/Git/repo_imported_new_github.png
[created-repoCLI]:     /assets/systemVersionSoftware/Git/repo_created_CLI.png
[conedImported-repo]:  /assets/systemVersionSoftware/Git/repo_cloned_imported_github.png
