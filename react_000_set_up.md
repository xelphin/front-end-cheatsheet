# React Set Up

## Set Up

1. `cd` into the folder where you want the project to appear and write:
```
$ npm create vite@latest my-first-react-app -- --template react
```
(press `y` and `enter` if needed)

2. Follow the steps:

```
$ cd my-first-react-app
$ npm install
$ npm run dev
```

3. On a browser, you can enter in the url: `http://localhost:5173/` and see the app

### More on Environment

#### Dev Tools Extensions
https://chromewebstore.google.com/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en

## Online Guides

https://react.dev/learn

## Deploying

https://vitejs.dev/guide/static-deploy.html

Can use one of the following:

### Netlify

https://www.netlify.com/

The most convenient way would be to directly import your GitHub repository to Netlify.

1. Push your React application to GitHub.
2. Import your project to Netlify by logging in, and selecting your repository. (https://app.netlify.com/start)
3. Select the branch to deploy from (the default setting, from `main`, works) and hit “Deploy site”!

### Vercel

https://vercel.com/

1. Push your React application to GitHub.
2. Import your project to Vercel. (https://vercel.com/new)
3. Vercel will automatically detect that you are using Vite. Set your name as you like, and hit “Deploy”!


### Cloudfare

https://pages.cloudflare.com/

1. Push your React application to GitHub.
2. Create a new Cloudflare account and log into it.
3. Under “Account Home”, select “Workers & Pages” > “Pages” > “Connect to Git”.
4. Connect to GitHub and select your GitHub repository.
5. Under “Set up builds and deployments”, set `npm run build` as the build command, and `dist` as the build output directory.
6. Under “Environment variables (advanced)” > “Add variable”, add a variable named `NODE_VERSION` and set its value to be the version number of Node that you are using. You can find this by executing `node -v` in your terminal.
7. Hit “Save and Deploy” and watch it come to life!