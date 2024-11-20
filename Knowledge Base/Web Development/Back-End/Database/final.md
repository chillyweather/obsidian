# Stage 1: Back End

Let's start with the back end. After all, that's how it's usually done: first, we create an API, then the front-end part to go along with it. You'll have a week to do it.

## Preparation

1.  Clone the back-end repository to your computer. Create a branch for the code of the first stage locally. Name it `stage-1`. Write all the code for the first stage in this branch.
2.  Add all necessary infrastructural project files: `.gitignore`, `.editorconfig`, `.eslintrc`. You can take these files from the "Around the U.S." project.
3.  Initialize `package.json`:
    -   Fill in the `name` and `author` fields as you wish.
    -   Fill the `scripts` section. It must contain the `dev` and `start` commands. `dev` starts the project in development mode with hot reload, and `start` runs it in production mode without hot reload.

## Create API Resource Schemas and Models

There are two entities in the project: `user` and `article`. Create a schema and model for each of them.

**`user` schema fields**:

-   **email** — the user's email which they use for registration. This field is required and should be unique to each user. It must also be validated against the email schema.
-   **password** — password hash. Required string. You need to set the default behavior so that the database doesn't return this field.
-   **name** — a username such as "Damien" or "Susie". String from 2 to 30 characters, required field.

**`article` schema fields**:

-   **keyword** — the word by which the articles are searched. A string, required field.
-   **title** — an article title (string, required).
-   **text** — the article text (string, required).
-   **date** — the article date (string, required).
-   **source** — the article source (string, required).
-   **link** — a link to the article (string, required, must be a URL address).
-   **image** — a link to the image for the article (string, required, must be a URL address).
-   **owner** — the _id of the user who saved the article. You need to set the default behavior so that the database doesn't return this field.

## Create Routes and Controllers

The following 4 routes should be in the API:

Copy codeBASH

`# returns information about the logged-in user (email and name)
GET /users/me

# returns all articles saved by the user
GET /articles

# creates an article with the passed
# keyword, title, text, date, source, link, and image in the body
POST /articles

# deletes the stored article by _id
DELETE /articles/articleId` 

Create a controller for each route. Protect the routes using authorization: if the client hasn't sent the proper JWT, access to the routes should be denied.

## Implement Authentication and Authorization

There should be two more routes in the API: registration and login.

Copy codeBASH

`# creates a user with the passed
# email, password, and name in the body
POST /signup

# checks the email and password passed in the body
# and returns a JWT
POST /signin` 

These two routes don't need to be protected by authorization.

## Implement Logging

Set up two files for storing logs:

-   `request.log` is for storing information about all API requests
-   `error.log` is for storing information about errors returned by the API

Logs must be in JSON format. Log files shouldn't be added to the repository.

## Deploy

1.  Create a server. Then install everything you need and deploy the API there.
    
    It is important to implement access to the API through a public IP address. Previously, we accessed the server locally with a localhost address. This is fine for the development process, but it won't work for production. This is because you're the only one who can access your localhost server. As such, if you want your website to be accessed by other people, the server needs to be located somewhere else.
    
    We recommend using Microsoft Azure to create a cloud server. It offers a free trial for new users.
    
2.  Create a domain and attach it to the server.
    
    Assign the public IP address of your server to the domain. A free domain will do. You can register it by [following this link](https://grabadomain.nomoreparties.site/). You already created a domain in the last sprint, so you should be familiar with the process.
    
    Readiness criterion: API can be accessed by the domain name.
    
3.  Issue certificates and attach them.
    
    It should be possible to access the server via https.
    
4.  Create an `.env` file on the server.
    
    Add environment variables to this file:
    
    -   `NODE_ENV=production`
    -   `JWT_SECRET` with a secret key for JWT creation and verification
        
        The `.env` file should be stored only on the server. You shouldn't store environment variables in the repository because it isn't safe.
        
        In development mode, the code should run and work without this file. Set the condition to run the dev build when `process.env.NODE_ENV !== 'production'`.
        
5.  Tell the world how to find your public server.
    
    Add a domain to the README.md file where you can access your server.
    

## A Few Tips

1.  Keep passwords encrypted.
2.  Validate the data that comes in the body and parameters of the request. If there is something wrong with the body, request processing shouldn't be passed to the controller at all. In this case, the client should receive an error.
3.  Handle errors centrally. At the end of the `app.js` file, add some middleware code for handling errors. If errors occur, don't return them to the client. Pass the handling to the centralized middleware instead.
4.  Pay attention to the status codes. You'll definitely need the following ones: `200`, `201`, `400`, `401`, `404`, `500`.
5.  Make sure that users can't delete articles saved by other users.

## What About the News Search?

You'll deal with this later. You'll use a third-party API for the search feature, so you'll implement it along with the rest of the front end. Your API is only responsible for authorization and storing articles.

## Once Everything's Ready

Submit the link for the pull request opened from the `stage-1` branch to `main` via the Practicum interface. You can paste the link into the following window:

![image](https://pictures.s3.yandex.net/resources/review_1605705914.jpg)

Note that you need to attach a link specifically to the pull request, not to the repository. Once the work is credited, click the "Merge" button to apply the changes from the `stage-1` branch to `main`.

Try to distribute the workload so that you have 2-3 days left to fix any issues that the reviewer picks up.

Give it your best shot and don't be nervous! All the tasks in your final project are manageable. We believe in you and wish you the best of luck.

## Assessment Criteria

Make sure to check your project against the checklist.

Final project evaluation criteria: [https://code.s3.yandex.net/web-developer/static/web-diploma-criteria-en/index.html](https://code.s3.yandex.net/web-developer/static/web-diploma-criteria-en/index.html)