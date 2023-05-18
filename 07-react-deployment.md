# React Deployment

| Term | Definition |
| ---- | ---------- |
| __Deployment__ | The process of making a software application available and accessible to users by hosting it on a server or online platform. |
| __Environmental variables__ | Variables that are used to configure and customize the behavior of an application based on the environment in which it is running. They can store sensitive information like API keys or database credentials. |
| __Continuous Deployment__ | A software development practice where changes to an application's codebase are automatically built, tested, and deployed to a production environment whenever a new commit is pushed to the repository. |

---

## Netlify Deployment Process

1. __Create a New Site__

    Once you're logged in, click on the "New site from Git" button on the Netlify dashboard. Select the Git provider (GitHub) and authorize Netlify to access your repositories.

    >There is an authorization option to share "all repos" rather than just one. We'll be deploying on Netlify a lot, so choose that option.

2. __Select your repository__

    Netlify will present you with a list of your GitHub repositories. Choose the one you want to deploy.

3. __Configure build settings__

    After selecting your repository, you'll be prompted to configure the build settings for your site. The default settings should work for most projects, but you can customize the build command and output directory if necessary. Netlify automatically detects common build tools and frameworks.


4. __*Optional*: Specify environment variables__

    If your project requires environment variables, you can specify them in the "Environment" section. This is useful for sensitive information like API keys or configuration options.

5. __Trigger the initial build__

    Once you've configured the build settings, click on the "Deploy site" button to trigger the initial build process. Netlify will clone your repository, install dependencies, and build your project.

6. __Monitor the build process__

    You can track the progress of the build on the Netlify dashboard. Netlify provides real-time logs and notifications, so you'll know if there are any issues during the build.

7. __Review the deployed site__

    Once the build is complete, Netlify will provide you with a URL for your deployed site. You can click on it to view your site and ensure everything is working as expected.

---

## Example .env file

- What type of information should you store in a `.env` file?
- What are some of the benefits of using a `.env` file to store this information?

```bash
REACT_APP_API_KEY=123456789
REACT_APP_API_URL=https://api.example.com
```

## Using environment variables in React

- What is `process`?
- The `fetch` snippet is a common pattern for what development action?

```js
const apiKey = process.env.REACT_APP_API_KEY;
const apiUrl = process.env.REACT_APP_API_URL;

// Use the variables in your code
fetch(apiUrl, {
  headers: {
    "Authorization": apiKey,
  },
});
```