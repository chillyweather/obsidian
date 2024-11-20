

# Deploying Your Project

The front-end part of the "Around the U.S." project is ready. But what's the point of doing all this if no one can see your site?

It's time to deploy the project, i.e. upload it to the server. Once you deploy the project, your site will appear on the internet and become available to users.

The deployment process often involves way more than simply uploading files to the server. It can include code transpilation, installing dependencies, and server-side scripting. This is why the term "deploy" was coined in the first place, rather than simply saying "upload to the server."

At the moment, your project only consists of a few static files, so we don't need to invoke the full magic of deployment just yet. However, we'll dive a lot deeper into this when we get to the back-end course.

## Hosting and GitHub Pages

You need a hosting service to publish a site on the internet. A host is the provider of the server on which your site will be uploaded. When working on real projects, developers need to make sure they choose a suitable host for their site as they vary in cost and capability.

However, for the projects you're working on in this program, GitHub Pages will do just fine. This is a service provided by GitHub that allows you to deploy your project directly from the GitHub repository.

## Setting Up GitHub Pages

To add a project to GitHub Pages, you need to create the `gh-pages` branch in the repository and upload the bundled project there. Alternatively, you can do this much easier by using a [special npm package](https://www.npmjs.com/package/gh-pages) named `gh-pages`.

1.  First of all, you need to install it:
    
     `npm install gh-pages --save-dev` 
    
    A new line will appear in the `package.json` file in the `devDependencies` section:
        
     `devDependencies: {
       ...
         "gh-pages": "^3.1.0"
       ...
     }` 
    
2.  In `package.json`, add a new script named `deploy`. This script will call the `gh-pages` package and transfer the folder containing the bundled project to it. In our case, this is the `dist` folder:
    
     `scripts: {
       ...
       "deploy": "gh-pages -d dist"
     }` 
    
3.  Usually, before deploying, we build the project with the `npm run build` command. Instead of doing this manually every time, you can tell NPM to call the `build` script before each invocation of the `deploy` script. To do that, simply add the `predeploy` script to the `scripts` section:
    
     `scripts: {
       ...
       "predeploy": "npm run build",
       "deploy": "gh-pages -d dist"
     }` 
    
    This script will be called whenever the `deploy` script is called.
    
4.  At this point, all the settings are ready, and all that's left is to run the `npm run deploy` command. When you do this, the project build will be created, and the contents of the `dist` folder will be moved to the remote `gh-pages` branch. If you see the following error:
    
     `Couldn't find remote ref refs/heads/gh-pages` 
    
    Run the `npx gh-pages-clean` command and repeat step 4.
    
5.  Go to your repo on GitHub and make sure that the `gh-pages` branch has appeared among other branches and contains your project build:
    

![image](https://pictures.s3.yandex.net/resources/deploy_1597674875.png)

6.  Go to your repo settings, scroll down to GitHub Pages section and change the source branch to `gh-pages`.
    
7.  After a few minutes, the site will be available at:
    
     `https://yourUsername.github.io/yourRepo` 
    
    Just replace `yourUsername` with your username and `yourRepo` with the name of your repository.
    

Now, whenever you make changes to your project, you can just call the `npm run deploy` command, and the changes will appear on your site.

Add a link to the site in the description of the repository on Github. This way, people visiting it can see not only the code but also the site itself and quickly test it. Easy!