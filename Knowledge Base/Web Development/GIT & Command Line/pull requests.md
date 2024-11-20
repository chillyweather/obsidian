# Pull Requests

[[Knowledge Base/Web Development/GIT & Command Line/git]]

By now, you should be familiar with Git branching. Branches are needed when several people are working on the same project. Each developer will have their own branch with their own version of the code where they can work independently from other members of the team. Moreover, working in a branch other than `main` prevents bad code from reaching production, i.e. the end user.

Let's say we are tasked with adding a new button to a dashboard. The first thing we'd do after cloning the project would be to create a new branch. Then, once we've built the button and tested it, we only need to move them from our fork to the `main` branch of the repository. To do this, we'll go to GitHub and take advantage of a convenient feature for working with a team: pull requests.

Whenever GitHub detects that it's possible to create a pull request from the current branch, the "Compare & pull request" button appears:

![image](https://pictures.s3.yandex.net/resources/github_mm_10_1605699546.jpg)

Click this button to go to the pull request creation screen. In the interface above the "Create pull request" button, we see a menu with branches and repositories.

It's important to remember that the branch on the left is the destination (where the changes will go) and the branch on the right is the source (the branch to take the changes from). The direction is also indicated by an arrow.

We can open a pull request between branches of the same repository.

Additionally, above the form, we can see the destination and source branches, and below the form, we can also see which files have been changed.

![image](https://pictures.s3.yandex.net/resources/github_mm_11_v02_1605699581.jpg)

Creating a pull request. In this interface, we can set destination and source branches, as well as the pull request title and description.

On this page, you'll need to give this change a name and briefly describe these changes. After that, we can click on the green "Create pull request" button.

This will create a pull request in the repository. Further, in the "Pull requests" tab, we can see the discussion of the proposed changes:

![image](https://pictures.s3.yandex.net/resources/Final_Project_08_1605699608.png)

_Discussion in the "Pull requests" tab_

The code reviewer may leave a comment here if there's something wrong with the code:

![image](https://pictures.s3.yandex.net/resources/Final_Project_10_1605699629.png)

_Our work isn't finished yet_

Once we finish fixing the code and make another commit, the changes will automatically be added to the pull request. They can be viewed in the "Commits" tab:

![image](https://pictures.s3.yandex.net/resources/github_mm_15_1605699649.jpg)

_Commit history in the "Commits" tab_

The new commit will automatically appear in the "Conversation" tab:

![image](https://pictures.s3.yandex.net/resources/Final_Project_10_1605699744.png)

_New commits are displayed in the "Conversation" tab_

When everyone has approved the code, the code reviewer (or the person overseeing the project) will press the "Merge" button and the changes will go to the `main` branch.