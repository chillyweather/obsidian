# Building a Project

Until now, we've been working with the development build of our project. This makes perfect sense, because our project actually is in development. But what do we do when we want to build it for production?

Inside of the `package.json` file that Create React App generated for us, we can see there are already a few scripts for us to use:

```json
// package.json

"scripts": {
  "start": "react-scripts start",
  "build": "react-scripts build",
  "test": "react-scripts test",
  "eject": "react-scripts eject",
}
```



We've already used the `"start"` script a number of times whenever we've wanted to run our project on the local host. So when we want to build our project, running the `"build"` script is a logical choice.

When we use the command `npm run build` in the terminal, the script will generate an optimized production build of your project. Practically speaking, this means that a new folder named `build/` will appear inside your project. Inside of `build/static`, you'll find optimized versions of all the code we've created as well as some other assets (JS, CSS, and fonts).

Then, these files can be deployed to any server where we can access them. In short, our app can use these files to deploy our web application on the internet.

Later in the program, we'll learn about one possible way to do this using NodeJS, but there are actually many possible ways to achieve this.

For the sake of demonstration, we can run the project from the `build/` folder from our local machine, but we'll need some additional tools.

From the command line, we'll run the following command: `npm i -g serve`. Just as we installed Create React App as a global command tool, we've now installed a package that will allow us to run our project from our local machine.

Assuming that we've already built the project by running `npm run build`, in the console, we can navigate inside of the project's main directory, and then we simply need to run `serve -s build`. We'll receive a prompt informing us that our project is now running on the local server. By default, this address will be `localhost:5000`. If we navigate here, we'll be able to see our project up and running, beautiful mattress and all.

If you're using macOS, install the package globally with `sudo npm i -g serve` and enter your password.

One last thing. Inside of `package.json`, there might be a property called `"homepage"`. As you might be able to guess from the name, when we host our projects online, we'll use this value to indicate the home address of our project.

Whenever you feel comfortable, it's time to move on.