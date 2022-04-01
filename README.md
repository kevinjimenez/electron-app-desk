# AppDesktop
Una aplicacion de escritorio realizada con electron y angular

instalar los paquetes:
- npm install --save-dev electron
- npm i --save-dev electron-packager
- npm i --save-dev @types/electron


añadir un script en el package.json

```"electron": "ng build && electron ."```

ademas añadir tambien
``` "main": "main.js", ```

crear un file main.js a la altura de package.json
 con el contenido

``` 
const { app, BrowserWindow } = require("electron");

let appWin;

createWindow = () => {
  appWin = new BrowserWindow({
    width: 800,
    height: 600,
    title: "Angular and Electron",
    resizable: false,
    fullscreenable: true,
    webPreferences: {
      nodeIntegration: true
    }
  });
  appWin.maximize();
  appWin.loadURL(`file://${__dirname}/dist/index.html`);

  appWin.setMenu(null);

  appWin.webContents.openDevTools();

  appWin.on("closed", () => {
    appWin = null;
  });
}

app.on("ready", createWindow);

app.on("window-all-closed", () => {
  if (process.platform !== "darwin") {
    app.quit();
  }
});
 ```


cambiar en el index.html
```<base href="/">``` por ```<base href="./">```

en el file angular.json cambiar
``` "outputPath": "dist/app-desktop", ``` por ```"outputPath": "dist",```
