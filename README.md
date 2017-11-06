# Electron + React boilerplate
A simple boilerplate that runs both Electron and React on the same application.

## How it works
It uses [create-react-app](https://github.com/facebookincubator/create-react-app) to create the basic React structure. Then it runs the Electron, loading the content of the React application (by default is configured to run the content of the http://localhost:3000).

## How to use
Clone the repo:
```bash
git clone https://github.com/lucasfrosty/electron-react-boilerplate
```
Then, install the dependencies:
```bash
yarn
```

Now, run the script(s). Here you have two options:
### 1. Run React and Electron in different scripts
#### ---- First you run React:
```bash
yarn react-start
```
This will run the React application on http://localhost:3000 (you can change the port on the package.json configs)
#### ---- Now, in another terminal, you run Electron:
```bash
yarn electron-start
```
This will run the Electron application **consuming** the React part being hosted (by the previous script). The order here is important; if you run the Electron first than React, the Electron app will not have the React part running to consume. So make sure to run the scripts in the correct order.
<br>


### 2. Run both React and Electron on the same script:
```bash
yarn start
```
This script is a like bit tricky. We'll be running both the ```react-start``` and ```electron-start``` scripts at the same time, but in this case we will using the [concurrently](https://www.npmjs.com/package/concurrently) and [wait-on](https://www.npmjs.com/package/wait-on) packages to make sure that the ```electron-start``` script will only run when the ```react-start``` (and the http://localhost:3000) script runs completely.

##### I am personally not a big fan of the 2nd approach because once you close the Electron application, you will need to restart both the Electron and the React server to run it again. While with the 1st approach, you have the concerns seperated to each script (and instance of terminal). But that's up to you.

## React and Redux devtools
This boilerplate also install [React](https://github.com/facebook/react-devtools) and [Redux](https://github.com/gaearon/redux-devtools) devtools into the Electron application using the [electron-devtools-installer](https://www.npmjs.com/package/electron-devtools-installer) package. If you don't want that in your application, make sure to disable this piece of code (line 31...35 on ``src/electron-starter.js``).

## Observations
As you can see, i use ```yarn``` to run the scripts. This is a personal preference. If you want to use npm instead of yarn, make sure to convert the yarn scripts to npm, [this can help you](https://yarnpkg.com/lang/en/docs/migrating-from-npm/).

## Reference(s)
1. [Building an Electron application with create-react-app](https://medium.freecodecamp.org/building-an-electron-application-with-create-react-app-97945861647c)
2. [DevTools Extension](https://github.com/electron/electron/blob/master/docs/tutorial/devtools-extension.md)
