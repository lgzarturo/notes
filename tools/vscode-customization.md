---
title: "Personaliza VSCode"
description: "Una forma de aumentar la productividad es conocer tus herramientas de trabajo, hay extensiones que te ayudan a escribir más rápido y te ayudan a mejorar tu productividad."
tags: themes
date: 2021-07-14
---

## Personalización

> Accede a los plugins desde la pagina del marketplace en el navegador, es mas comodo y mas sencillo para navegar. <https://marketplace.visualstudio.com>

### Temas

Instalar un tema que se adapte a tus necesidades y gustos

Recomendados:

- [Cobalt2 Theme - Wes Bos](https://github.com/wesbos/cobalt2-vscode)
- [Atom - Mahmoud Ali](https://github.com/akamud/vscode-theme-onedark)
- [Winter is comming - John Papa](https://github.com/johnpapa/vscode-winteriscoming)
- [The Lone Coder - Me](the-lone-coder-theme-for-vscode.md)

### Tema de iconos

- [Material Icons Theme - Philipp Kief](https://github.com/PKief/vscode-material-icon-theme)

### Font Ligatures

Para usar la propiedad de Font Ligatures es necesario instalar una fuente que soporte esa características. Un tipo de fuente muy popular es la fuente [FiraCode](https://github.com/tonsky/FiraCode)

Fuentes populares:

- <https://github.com/tonsky/FiraCode>
- <https://github.com/belluzj/fantasque-sans>
- [https://github.com/ryanoasis/nerd-fonts](https://github.com/ryanoasis/nerd-fonts)

(Command + ,) Para acceder al panel de configuración.

User settings

```json
"editor.fontFamily": "Operator Mono, Fira Code, Menlo, Inconsolata",

"editor.fontLigatures": true,
```

- Otras opciones interesantes.

    ```json
    "window.zoomLevel": 4,
    "editor.autoIndent": true,
    "editor.codeLens": false,
    "editor.cursorBlinking": "smooth",
    "editor.cursorStyle": "underline-thin",
    "editor.fontSize": 16,
    "editor.formatOnPaste": false,
    "editor.formatOnType": false,
    "editor.formatOnSave": true,
    "editor.letterSpacing": 0.5,
    "editor.lineHeight": 25,
    "editor.tabSize": 2,
    "editor.formatOnSave": true,
    "editor.wordBasedSuggestions": false,
    "editor.renderWhitespace": "none",
    "editor.tabCompletion": true,
    "editor.wordWrap": "off",
    "editor.quickSuggestions": {
     "other": true,
     "commentes": false,
     "strings": true
    },
    "emmet.includeLanguages": {
     "javascript": "javascriptract",
     "markdown": "html"
    }
    "explorer.confirmDragAndDrop": false,
    "explorer.openEditors.visible": 0,
    "extensions.ignoreRecommendations": true,
    "extensions.autoUpdate": false,
    "files.autoSave": "afterDelay",
    "files.autoSaveDelay": 1000,
    "files.exlude": {
     "**/.git": true,
     "**/.DS_Store": true,
     "**/*.js": {
      "when": "$(basename).ts"
     }
    }
    "html.format.extraLiners": "",
    "git.enableSmartCommit": true,
    "git.confirmSync": false,
    "git.autofetch": true,
    "search.exclude": {
     "**/node_modules": true,
     "**/bower_components": true,
     "**/jspm_packages": true,
     "**/dist": true,
     ".git": true,
     ".idea": true,
    }

    ```

### Respaldar la configuración

Es necesario instalar la extensión:

- Settings Sync - Shan Khan

> Mi configuración esta en este Gist [b358672f882f22841567bc0755629050](https://www.notion.so/b358672f882f22841567bc0755629050)

(Command+Shift+P) : Seleccionar la opción "Sync: Update/Upload Settings" para que se genere una configuración basada en GitHub Gist.

## Mejorar la productividad

```json
"files.autoSave": "afterDelay",
"files.autoSaveDelay": 1000,
```

**Insertar las medidas de una imagen en la etiqueta <img>**

(Command+P) Selecciona la opción: Emmet: update image size

### Extensiones para mejorar el desarrollo

- [Angular Snippets (Version 12)](https://github.com/johnpapa/vscode-angular-snippets)
- [Angulas Essentials (Extension Pack) - John Papa](https://github.com/johnpapa/vscode-angular-essentials)
- [Vue VSCode Snippets - Sarah Drasner](https://github.com/sdras/vue-vscode-snippets)
- [Vetur - Pine Wu](https://github.com/vuejs/vetur)
- [Vue VS Code (Extension Pack) - Sarah Drasner](https://github.com/sdras/vue-vscode-extensionpack)
- [React Food Truck - Burke Holland](https://github.com/burkeholland/react-food-truck)

## Trabajando con el código

- (Command+P+P) Cambio entre los dos últimos archivos.
- (Shift+F12) Buscar referencias en el código.
- (Command+Shift+O) Buscar símbolos en el código por jerarquía.
- (Command+B) Abrir y cerrar el listado de archivos.
- (Command+`) Abrir y cerrar la terminal

### Code Formatter

[Prettier extension - Esben Petersen](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

Command+Shift+F

```json
"prettier.bracketSpacing": true,
"prettier.printWidth": 100,
"prettier.singleQuote": true,
"prettier.eslintIntegration": true,
"prettier.tabWidth": 2,
```

[ESLint - Dirk Baeumer](https://github.com/Microsoft/vscode-eslint)

## Debugging

Habilitar la comprobación de sintaxis en JavaScript

//@ts-check

O agrega la siguiente propiedad en los settings.

```json
"javascript.implicitProjectConfig.checkJs": true
```

## Extensiones Recomendadas

- [Paste JSON - Quicktype](https://github.com/ZainChen/vscode-json)
- [TODO Highlight](https://github.com/wayou/vscode-todo-highlight)
- [TODO Tree](https://github.com/Gruntfuggly/todo-tree)
- [Bookmarks](https://github.com/alefragnani/vscode-bookmarks)
- [Bracket Pair Colorizer 2](https://github.com/CoenraadS/Bracket-Pair-Colorizer-2)

## Enlaces

[https://www.vscodecandothat.com/](https://www.vscodecandothat.com/)
