---
title: "Empieza con Amplify, fácil y sin complicaciones"
description: "Amplify propone un entorno de desarrollo en la nube, como una solución de desarrollo automatizando el despliegue de software."
tags: backend
---

## Crear una aplicación con React

Como primer paso es necesario crear una aplicación base de React, que será el proyecto con el que vamos a trabajar

```bash
npx create-react-app landings-api --use-npm
```

### Instalar las dependencias

Se requiere de la instalación de las dependencias de Amplify y el paquete de UI para React

```bash
npm i aws-amplify @aws-amplify/ui-react
```

### Iniciando Amplify

Creamos el proyecto de tipo Amplify, con el que se debe configurar la aplicación del backend y se sincronizara con los recursos en la cuenta de AWS

```bash
amplify init
? nameapp
? dev
? Visual Studio Code
? javascript
? react
? build
? npm run-script build
? npm run-script start
aws profile
? Y
? default
```

## Agregar seguridad con Cognito

```bash
amplify add auth
? Default configuration
? Username
? Yes, i want to make some additional changes
? Defaults
```

### Publicando los recursos en AWS

```bash
amplify push
? Y
```

### Editando el código

```bash
code .
```

### Editar el archivo `App.js`

```javascript
import Amplify from 'aws-amplify'
import aws-config from './aws-exports'
import {withAuthenticator, AmplifySingOut} from '@aws-amplify/ui-react'

Amplify.configure(aws-config)
...
<AmplifySingOut />
...
exports default withAuthenticator(App)
```

## Crear un API Rest

```bash
amplify add api
? Rest
? landingsapi
? /api/v1/landings
? Create a new lambda function
? landingsfunction
? landingsfunction
? nodejs
? CRUD function for DynamoDB
? create a new DynamoDB table
? landingsdb
? landingsdb
```

> Definir las columnas de la tabla
> ? title
> ? string
> ? partition key for the table: title
> ? add sort key for your table: yes
> ? choose field?
> ? secondary indexes? no
> ? lambda trigger? no
> ? other resources? no
> ? invoke this function on recurring schedule? no
> ? edit the local lambda function now? Yes

### Editar el código generado

> amplify/backend/function/landingsfunction/src/app.js

```javascript
...
const useIdPresent = true
...

/* HTTP Get method for list objects

- dynamodb.query(queryParams ...
+ dynamodb.scan(queryParams ...
```

### Seguimos con el flujo del API rest

```bash
? restrict api access? Y
? select all crud operations
? another path? No
```

### Publicando cambios

```bash
amplify push
```

## Desarrollando en `App.js`

```javascript
import React, {useEffect, useState} from 'react'
import Amplify, {API} from 'aws-amplify'

...
  const [title, setTitle] = useState('')
  const [pages, setPages] = useState([])
  useEffect(() => {
    API.get('landingsapi', '/landings/title').then((pagesResponse) => {
      setPages([...pages, ...pagesResponse])
    })
  }, [])

  const handleSubmit = e => {
    e.preventDefault()
    API.post('landingsapi', '/landings', {
      body: {
        title,
      }
    }).then(fetchedPage => {
      setPets([fetchedPage, ...pages])
    })
  }

  <form onSubmit={handleSubmit}>
    <input value={title} placeholder='' onChange={(e) => setTitle(e.target.value)} />
    <button type="submit">Guardar</button>
  </form>

  <ul>
    {pages.map(page => <li>{page.title}</li>)}
  </ul>
...
```
