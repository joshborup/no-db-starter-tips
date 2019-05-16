# **These are a few tips for getting an App up and running**

total file structure
<span id='fun'></span>

```
my-project/
    node_modules/
    public/
    server/
        index.js
        customData.json
        controller/
            controller.js
    src/
        components/
            MyComponent/
                MyComponent.js
                MyComponent.css
        App.js
        index.js
        setupProxy.js
        index.css
        App.css
    .gitignore
    package.json
```

`node_modules`: where everything from NPM is installed and lives, dont worry about this folder

`public`: Where html file react atttaches to lives, you can changes the title and meta tags of your app here

`customData.json`: if you need data to work with, you can paste a json object/array of objects in a .json file and just require it in any folder you need. Node nativley exports all json files so you dont need to do a `module.exports`

`setupProxy.js`: this is a config file for reacts development server, this file must be spelled in camelcase as the dev server looks for the file by name. In order to hit your node server in development, you will place proxies in this folder that will route all `/api` requests to the port your node server is running on

`index.css`: You should always add a reset file to the projects you are working on. you can replace all of the default contents with a [Reset](https://cssreset.com/scripts/eric-meyer-reset-css/)

Tip: Remember to add the following to the bottom of your CSS file to make width and height measurements include the border and padding

```css
html {
  box-sizing: border-box;
}

* {
  box-sizing: inherit;
}
```

`.gitignore`: This file will tell git which files it should ignore when you are committing. typically node_modules and password files go here.

Tip: Double check node_modules is added

`package.json`: This file holds configurations and information about our application like the npm modules we are using in our app, and what to do when

# Project Launch

## Steps:

- in the terminal, run `create-react-app my-project`
- `cd` into `my-project` and type '`code .`' to launch your project in VScode
- delete everything out of index.css and paste in your reset
- create your server file as a sibling directory to src/ [reference total folder structure](#fun)
- in the server folder

  - make an `index.js`, this will be your server file
  - make a `controller` directory with a `controller.js`
  - in the terminal `npm i express` and require `express` at the top of `index.js`
  - decalre `app` and set it equal to `express()`
  - call `app.use(express.json())` to use body requests
  - declare `port` (typically 4000)
  - call `app.listen()` and pass in your port and a callback
  - declare `app.get()` pass in the `/api` path you would like to use and your enpoint handler function.
  - run nodemon, check your browser that the endpoint is live

- in src/
  - add a setupProxy.js so that your frontend can make requests to your node server
  - create a class based component
  - `npm i axios`
  - `import` axios at the top of your component
  - in a `componentDidMount` call a get method with axios and pass in the `/api` path you setup on your node server.
  - import and render your class component in `App.js`
  - console log the `response` and check the console that the data is coming through
