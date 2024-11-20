# Subjects to Master

In addition to core JS/CSS/HTML skills, there are a lot of dev skills and workflows that are related to open source contributions. Let's talk about the big ones that you'll need.

Familiarity with Git, GitHub/GitLab, packaging managers, and semantic versioning is a good idea. It's also great to know about code formatting and testing because, when delivering your contributions, you'll need to do it in the requested format.

### First things first

**Git / GitHub**

In general, the ability to use the Git version control system is an essential prerequisite when entering the world of development. For open source contributions, you'll need a decent knowledge of things like the general [GitHub flow](https://guides.github.com/introduction/flow/), hooks, and commit signatures. You'll also need familiarity with the basic interface of GitHub or GitLab — particularly history navigation, blame view, pull request review, comments and checks, issue labels, and GitHub bots. When it comes to automating, customizing, and executing workflows in GitHub, you'll need to know how to use [GitHub Actions](https://docs.github.com/en/actions) or an alternative, such as [Travis](https://docs.travis-ci.com/user/tutorial/#to-get-started-with-travis-ci-using-github) or [Jenkins](https://www.jenkins.io/). You'll need to know how they trigger events for notifications and how to work in an isolated environment.

**Package managers**

Most JS apps are built with the help of many developers. This type of collaboration is made possible by shared libraries. We refer to multiple libraries together as a package. When we have a repository containing multiple packages, we'll need to use some kind of package manager to deploy the app.

Some of the most popular programs for this include [NPM](https://www.npmjs.com/) (Node Package Manager) and [Yarn](https://yarnpkg.com/) (built by Facebook, Google, Exponent, and Tilde). There's also an optimization tool for working with both NPM and Yarn called [Lerna](https://lerna.js.org/). It's mostly used in larger projects as they become hard to maintain over time, and this tool allows developers to modularize their code into smaller manageable repositories and extract shareable code which can be used across sub repos.

**Semantic versioning (SemVer)**

We need to be able to keep track of all the changes and progress we make to our products with each release. The most common way to do this is with [semantic versioning](https://docs.npmjs.com/about-semantic-versioning).

We use three numbers when naming a version, and the format looks like this: `Z.Y.X`. The value of `Z` is incremented for major changes, the value at `Y` is increased for minor changes, while the `X` value goes up for patches (bug fixes).

For instance, a product that has a version of `1.0.0` would be the very first release. If you made a minor bug fix for this, you would then release version `1.0.1`. Then, if you make a more significant update that is still backwards compatible with the original version, you would name this version `1.1.1`. If you then make a major update to your app that is not backwards compatible with the original version, you would release version `2.0.0`.

**Markdown syntax for documentation**

When dealing with GitHub/GitLab repos, it's important to know the basic [markdown](https://www.markdownguide.org/basic-syntax/) rules for `README` files and comments.

We can use [markdown syntax](https://guides.github.com/features/mastering-markdown/) to style text on the GitHub platform. It can change how text is displayed, format words as bold or italic, add images, create lists, and so on.

**Tools for code formatting and testing**

There are a number of tools for each language that analyze the source code and flag programming errors, bugs, stylistic errors, and suspicious constructions. These are called [linters](https://github.com/collections/clean-code-linters). For analyzing JS code we can use [ESLint](https://eslint.org/), [JSLint](https://www.jslint.com/), [JSHint](https://jshint.com/), and [Standard JS](https://standardjs.com/) among many others. One more useful tool when working with code is [Prettier](https://prettier.io/). It's a code formatter that supports a lot of languages. The best thing about it is that it formats your code automatically.

Many projects won't approve your pull request unless it has sufficient test coverage — so they need to be tested. Some popular testing frameworks for JS are [Jest](https://jestjs.io/), [Mocha](https://mochajs.org/), [Jasmine](https://jasmine.github.io/), and [Puppeteer](https://pptr.dev/).

### What's next?

The following list will come in handy if you want to get more serious about open source contributions and working in a team, especially if you decide to pursue a career as a front-end engineer.

**TypeScript language**

Once you're comfortable with JavaScript, you might want to learn a superset of the language: [TypeScript](https://www.typescriptlang.org/). It's a pure object-oriented programming language that supports classes, interfaces, etc. TypeScript is an open-source language that statically compiles the code to JavaScript. It can easily be run via Node.js.

**App development software**

[Docker](https://www.docker.com/) and [Netlify](http://www.netlify.com/) are both widely used in the front-end world — Docker for development, and Netlify for deployment. There are also alternatives to Netlify, such as [GitHub Pages](https://pages.github.com/) or [GitLab Pages](https://docs.gitlab.com/ee/user/project/pages/).

**Dependencies**

A dependency is a piece of third-party code that your application cannot function without. You need to be able to install, manage, run, and debug dependencies using tools like `package.json` scripts, code navigation settings in the integrated development environment (IDE) for setup, and NPM link.

**Sandbox environment**

Last but not least, let's talk about what you need to actually run an app. A sandbox environment is an isolated virtual machine in which potentially unsafe software code can execute without affecting network resources or local applications. Front-end live sandboxes such as the online code editor [CodePen](https://codepen.io/) and other more complex tools allow you to build apps faster as they allow you to write code in the browser, and see the results instantly.

### Extra tools

There are some other tools that are equally popular amongst all kinds of companies, remote teams, and open-source communities. Rather than being directly related to coding, these tools are more supplementary and support the surrounding ecosystem within which these communities operate.

**Communication and project management tools**

For communication, we use Slack, Gitter, and Discord. Trello, Jira, or alternative kanban services help track development cycles or sprints.

**Digital product design and mockups**

All products have an interface created by digital designers, and when you're actually working on bringing those designs to life as a developer, it's important to be able to work with mockups in the most popular services, including [Sketch](https://www.sketch.com/), [inVision](https://www.invisionapp.com/), and [Figma](https://www.figma.com/).