# Práctica del módulo configuración de servidores y despliegue de aplicaciones

## Ejercicio 1

En la dirección: node.tecnoox.com se puede visualizar la respuesta del ejercicio 1.

## Ejercicio 2

La dirección IP del servidor es: 3.20.140.143

En la dirección se muestra el resultado de la práctica realizada como parte del módulo de Fundamentos de HTML y CCS3.

En la dirección: tecnoox.com se puede visualizar la misma práctica anteriormente referenciada. En esta ocasión empleando protocolo https.

Con una dirección de correo electrónico y cualquier contraseña se puede entrar al resto de la página.

## Extra

En la dirección: odoo.tecnoox.com se puede visualizar el despleigue de odoo en el servidor.


## A continuación se encuentra el README de la aplicación desplegada en el ejercicio 1 

# NodePop

[Demo](/anuncios) of the methods (this link works only if you run the project)

Api for the iOS/Android apps.

## Deploy

### Install dependencies

    npm install

### Configure

Review lib/connectMongoose.js to set database configuration

### Init database

    npm run installDB

## Start

To start a single instance:

    npm start

To start in development mode:

    npm run dev (including nodemon & debug log)

## Test

    npm test (pending to create, the client specified not to do now)

## JSHint & JSCS

    npm run hints

## API v1 info

### Base Path

The API can be used with the path:
[API V1](/apiv1/anuncios)

### Error example

    {
      "ok": false,
      "error": {
        "code": 401,
        "message": "This is the error message."
      }
    }

### GET /anuncios

**Input Query**:

start: {int} skip records
limit: {int} limit to records
sort: {string} field name to sort by
includeTotal: {bool} whether to include the count of total records without filters
tag: {string} tag name to filter
venta: {bool} filter by venta or not
precio: {range} filter by price range, examples 10-90, -90, 10-
nombre: {string} filter names beginning with the string

Input query example: ?start=0&limit=2&sort=precio&includeTotal=true&tag=mobile&venta=true&precio=-90&nombre=bi

**Result:**

    {
      "ok": true,
      "result": {
        "rows": [
          {
            "_id": "55fd9abda8cd1d9a240c8230",
            "nombre": "iPhone 3GS",
            "venta": false,
            "precio": 50,
            "foto": "/images/anuncios/iphone.png",
            "__v": 0,
            "tags": [
              "lifestyle",
              "mobile"
            ]
          }
        ],
        "total": 1
      }
    }

### GET /anuncios/tags

Return the list of available tags for the resource anuncios.

**Result:**

    {
      "ok": true,
      "allowed_tags": [
        "work",
        "lifestyle",
        "motor",
        "mobile"
      ]
    }
