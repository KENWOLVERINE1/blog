---
draft: false
title: 'Life calendar widget log4'
---
## log 4:-

## Bundling the project as a distributable:-

Now electron doesn't have any tools for packaging and bundling in it's default core modules so, we need to install additional tools to create a packaged app that we can distribute to users either as a installer(MSI on windows) or portable executable file(.app on mac os) or as packages(snap,RPM,deb for multiple linux environments)

There are two ways to build the electron application by using `electron-forge` and `electron-builder`. I am going to use `electron-forge` since it is easy to create a bundle and it's is used in the official Docs but feel free to use what you prefer.

## Importing project inside forge:-

First we need to install forge and then import our project inside it
```sh
npm install --save-dev @electron-forge/cli
npx electron-forge import
```

Once we run the `electron-forge` there will be few scripts added to our `package.json`
```json
 //...
  "scripts": {
    "start": "electron-forge start",
    "package": "electron-forge package",
    "make": "electron-forge make"
  },
  //...
```

we can also see that few more packages are added under our dev dependencies and a new file named forge.config.js has been created.

## Creating a distributable:-

>**Note**: Since i am using fedora linux environment i will be making the distributable for RPM(Redhat Package Manager) but you guys can create your own distributable suitable to your environment or your targeted environment

Before we create a RPM package of our electron App we need to satisfy few requirements 

# Requirements:-

fist we need to install rpm-build to create a RPM package

If you are using a fedora environment
```sh
sudo dnf install rpm-build
```
if you are using debian or ubuntu
```sh
sudo apt-get insatll rpm
```

# Installation:-

```sh
npm install --save-dev @electron-forge/maker-rpm
```

# Usage:-

To use `@electron-forge/maker-rpm` we need to add it to our `forge.config.js` file under `makers`

```js
module.exports = {
  makers: [
    {
      name: '@electron-forge/maker-rpm',
      config: {
        options: {
          name:"life-calendar-widget",
          version:"1.0.0";
          license:"MIT";
        }
      }
    }
  ]
};
```
# Create the distributable:-

```sh
npm run make
```
THis command executes two steps namely 
1. `electron-forge package` under the hood to bundle our app in `electron binary` and generate the packaged code into a folder
2. Then it will used the packaged app folder to create seperate distributables for each configured makers.

>**Note**: You can have multiple makers inside the forge.config.js file to support all the targeted environments

The distributable will be located under `out/make` folder ready to launch!

And hence we have created our electron app successfully and created a distribuable file for other users as well

