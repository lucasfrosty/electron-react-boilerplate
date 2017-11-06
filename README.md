# Electron + React boilerplate
A simple boilerplate that runs both Electron and React on the same application.

## How it works
It uses [create-react-app](https://github.com/facebookincubator/create-react-app) to create the basic React structure. Then it runs the Electron, loading the content of the React application (here is configured to run the content of the http://localhost:3000).

## How to use
Clone the repo:
```bash
git clone https://github.com/lucasfrosty/electron-react-boilerplate
```
Then, install the dependencies:
```bash
npm install
```

Now, run the script(s). Here you have two options:
### 1. Run React and Electron in different scripts
- #### First ou run the React:
```bash
npm run react-start
```
This will run the React application on http://localhost:3000 (you can change the port on the package.json configs)
- #### Now, in order terminal, you run the Electron:
```bash
npm run electron-start
```
This will run the Electron application **consuming** the React part being hosted (in the previous script) on localhost:3000. The order here is important, if you run the Electron first than React, the Electron application will not have the React application running to consume.



### 2. Run both React and Electron on the same script:
```bash
npm run start
```
This script is a like bit tricky. We'll be running both the ```react-start``` and ```electron-start``` scripts at the same time, but in this case we will using the [concurrently](https://www.npmjs.com/package/concurrently) and [wait-on](https://www.npmjs.com/package/wait-on) packages to make sure that the the ```electron-start``` script will only run when the ```react-start``` (and the http://localhost:3000) script runs completely.

#### I am personally not a big fan of the 2nd approach because once you close the Electron application, you will need to restart both the Electron and the React server to run it again. While with the 1st approach, you have the concerns seperated to each script (and instance of terminal).


## Observations
Although the fact that i use ```npm``` on the documentation, you'll see that i use ```yarn``` to run the scripts, since i prefer. But if you want to use npm instead of yarn, make sure to convert the yarn scripts to npm, [this can help you](https://yarnpkg.com/lang/en/docs/migrating-from-npm/).