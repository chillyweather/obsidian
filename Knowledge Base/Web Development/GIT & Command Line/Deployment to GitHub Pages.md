# Deployment to GitHub Pages

[[Knowledge Base/Web Development/GIT & Command Line/git]]
[[Deployment]]


By default, GitHub Pages ignores files with names starting with the underscore (`_`). This is what many BEM file names start with. This problem can be solved by simply adding a file named `.nojekyll`.

Create an empty file named `.nojekyll` in the project root directory. Let's recall that all files starting with a period are hidden in Git.

```bash
pwd
/Users/students-yandex/dev/web_project_3

git branch
* main
develop

touch .nojekyll # created an empty file named .nojekyll
git add . && git commit -m "added nojekyll"

git push
```

make repository public

![[Pasted image 20210802192743.png]]
![[Pasted image 20210802192754.png]]

Scroll the page a bit higher to find the ”Source“ section. Select the branch with the code you want to publish in the dropdown menu. It can be the `main` branch:

![[Pasted image 20210802192834.png]]
![[Pasted image 20210802192852.png]]

![[Pasted image 20210802193043.png]]