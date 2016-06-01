# Git Forking, Cloning, and Pull Requests

## Overview

In this lesson we will learn how to fork, clone, and submit pull requests. These are the staples of the code collaboration lifecycle on Github.

## Objectives

1. Forking repositories.
2. Cloning respositories.
3. Making pull requests.

## Code Collaboration Through Github

Watch the video below if you are unfamiliar with Git. We will be using Git to access course materials and to share and collaborate on project code throughout this course. After watching the video you may use the text below to review all of the topics discussed in the video.

<iframe width="640" height="360" src="https://www.youtube.com/embed/videoseries?list=PLj148bJp5wiz3q3iuLp6eZrW6Iyjo7t-Y" frameborder="0" allowfullscreen></iframe>

### What is Cloning?

Cloning is the process of copying a remote repository down to your local filesystem. This could be a copy made from a new repository you make on your own Github account, or it could be an existing repository you come across. THe following instructions differ slightly from the video posted above, but the process and the principles are the same.

### Cloning A Repo From Github

To get started open your browser and head to Github.com. Click the `+` plus icon at top right and select new repository. Then name the repository `my-new-project` and click the **Create repository** button. Copy the SSH or HTTP clone url located at the top of the repository page. This step is the same whether it is anew repository or an existing one you wish to copy. Then open Terminal and navigate to the location on your filesystem where you wish the repo to be located. In the video example above I choose my `dev` folder. Note that when you clone a repository it will automatically create a folder for the repo with the same name as the repository. Now we clone by typing the command `git clone <paste in the repo url here>` and press return. Remember that SSH or HTTPS url you copied from the repo on Github? This url is pasted after  the command "git clone " using Command+v on mac or Ctrl+v for pc. Mine looked like this: `git clone git@github.com:jongrover/my-new-project.git`.  This tells git the location of the repository you are cloning and is a crucial step. This should output the following response:

```shell
Cloning into 'my-new-project'...
warning: You appear to have cloned an empty repository.
Checking connectivity... done.
```

If there had been content in the repo you would have seen more details such as the objects it downloaded as well.

Now if we type `ls` to list our files and folder we see that there is a new folder called "my-new-project". Then we can change directory `cd my-new-project` and press return to move into that repo. Now we can continue to work on this repository same as the others before: staging,commiting content, pushing, and pulling to our remote. Once nice thing is that since we cloned this repo it will have all the content the remote did as this is an exact copy. It will have the master branch, as well as any previous commit information that can be seen by typing `git log`. It is also already linked back to our remote "origin". 

Cloning is a great way to make a local copy of your own content. If for example you have two computers and you wish to keep your code in sync between the two. It is as easy as creating a remote on your Github account, then cloning from both computers. Then when you are working on computer A you can push up your changes and then on computer B you can pull those changes down (more on pulling coming up in a bit).

Cloning as mentioned is good for making copies of your personal repositories, however if you clone someone elses repository then you are limited to just reading from it (pulling), you will not be able to write (push) to someone elses repository as you have limited permissions on other peoples repos. This is for a good reason, as you wouldn't want other people writing changes to your own personal code without your say so. For open source projects the solution for allowing code collaboration but maintaining an owners rights to decide what code is changed comes through the process of forking and pull requests which we will discuss next.

### What is Forking?

Forking is the process of making a copy from someone elses remote repo to your own remote repo. So in contrast where cloning is making a copy from remote to local, forking is making a copy from a remote to another remote. You can also think of cloning as a personal action where as forking is much more a social action. Forking is a very common part of the open source code collaboration process. In most cases someone or a group who owns a code repo that is made available for public use, likes to allow other developers to contribute updates to their code. As the owner they want to be able to have the benefit of merging in good code, but preventing ding dongs and nit wits from posting bad code decisions to their repo. Forking allows anyone to copy the code to their own remote and do whatever they want to their copy, keeping the original repo untouched by others. Then collaborators are able to submit pull requests to offer their changes to be merged into the original owners code. We'll talk more about the pull rquest proecess coming up in a bit, but for now let's focus on the first step which is forking!

### Forking A Remote Repo On Github

There is a lot of exciting code we can fork on Github. For this example though let's open up our browser paste in the url to visit this repo here: [https://github.com/flatiron-school/fork-me-express-train](https://github.com/flatiron-school/fork-me-express-train). Next, click the Fork button located at the top right just below your Github avatar icon. Up pops a window that asks you to select where you would like to fork this repo to. Go ahead and select your personal profile icon at top left. This makes a copy from "flatiron-school/fork-me-express-train" to your own personal Github "<github-username>/fork-me-express-train". Now we have our own remote copy we can read and write to without damaging the original "flatiron-school" copy we forked from.

Now we woukld like to work on this locally so we need to clone from our forked copy. This process is just the same as we did for the last clone. We copy either the SSH or HTTPS clone url and head back over to Terminal. Navigate to the palce on your computer where you would like this repo to exist. for mine I went into my `dev` folder via `cd dev`. Now type in `git clone <paste-your-clone-url-here>` substituing your own clone url by pasting it in, and then press return. This will clone your remote forked copy down to your local filesystem.

Next, cd into the repo `cd fork-me-express-train`. Now let's make some changes. Feel free to go into any of the text below the heading "About Trains" and stuff and edit some text. Get creative, it won't hurt anything so type in whatever you like. Let's keep it G rated though please, the Learn.co platform is for all ages. Then save the file, `git add README.md`, `git commit -m "updated train text"`, `git push origin master`. Now we have updated our remote copy.

Whats left, is to share our updates with the owner of the original "flatiron-school" repo that we forked from. To do so we will make a pull request.

### Pull Requests

A pull request is simply a comparison from one branch to another that allows the owner of a repository to review the changes between those two branches and decide to merge the branches or close the request without merging. The comparison can be between branches of the same repo or the comparison can be made "across forks" meaning from one remote repository to another. In our case we would like to compare flatiron-school/fork-me-express-train master branch with our &lt;your-github-username&gt;/fork-me-express-train master branch.

First, let's head to our browser and go to your personal copy on Github.com at &lt;your-github-username&gt;/fork-me-express-train. Then click the green button at the top left of the page titled **New pull request**. This will automatically setup a new pull request between your master branch and the master branch that your forked from "flatiron-school"s. On the next screen click the green button **Create pull request** and then click **Create pull request** again. That's it. Now it up to the repository own of "flatiron-school". They will get a notice and check out your changes. If they like it they can merge in your code, otherwise they can start a dialogue with you asking you to make further changes before they accept, or they can simply close the request if they do not want to include those changes.

## Summary

- Forking allows us to make a copy from someone elses remote to our own remote. You initiate this by clicking the Fork button on any public repository on Github.com
- Cloning is the process of making a local copy from a remote repo. Use the command `git clone <repo-url-pasted-here>`.
- Making a pull request is the process of offering changes to code that you forked. It is a comparison between your branch and another. On a forked repository you can click the **New pull request** button to initiate it.

## Resources

- [Github Articles- Forking](https://help.github.com/articles/fork-a-repo/)
- [Git Docs - Cloning](https://git-scm.com/docs/git-clone)
- [Github Articles - Pull Requests](https://help.github.com/articles/using-pull-requests/)
- [Git Cheatsheet](https://www.git-tower.com/blog/content/posts/54-git-cheat-sheet/git-cheat-sheet-large01.png)
- [Git Best Practices](https://www.git-tower.com/blog/content/posts/54-git-cheat-sheet/git-cheat-sheet-large02.png)


<p class='util--hide'>View <a href='https://learn.co/lessons/html-css-git-forking-cloning-and-pull-requests'>HTML CSS Git Forking, Cloning, and Pull Requests</a> on Learn.co and start learning to code for free.</p>
