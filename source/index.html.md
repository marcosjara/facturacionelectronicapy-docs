---
title: Referencia de la API - FacturAPI

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript
  - java
  - vb

toc_footers:
  - <a href='#'>FacturApi Login</a>
  - <a href='https://facturapy.web.app'>FacturApi Home</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentacion de FacturApi
---

# Introduccion
Bienvenido a la documentacion de referencia de FacturApi, con el cual podras implementar rapidamente la comunicacion con el Sistema de Facturacion Electronica Nacional (Sifen) y podras emitir Documentos electronicos de forma segura para tus Clientes o para tu Empresa

## Que es FacturApi 
FacturApi es una plataforma compuesta de una Aplicacion Web y funciones a nivel de servicios de programacion que puden ser invocados mediante llamadas a API REST, el cual facilitan la integracion de tu Sistema o Aplicativo con el fin de emitir documentos electronicos (Facturas, Autofacturas, Notas de Debitos y Creditos y Notas de retencion electronicas), validados por la SET

FacturApi contempla todos los procesos requeridos para la generacion de documentos electronicos.

1. Generacion del Documento XML segun el manual tecnico de la SET
2. Firma del Documento Electronico, utilizando el certificado digital de la Empresa contribuyente
3. Generacion del Codigo QR para la Factura.
4. Comunicacion con la SET (Envio de documentos electronicos, generacion de lotes de envio, consulta de documentos.)
5. Generacion del Documento KUDE (Archivo PDF de la Factura o Documento electronico, personalizado de acuerdo al Logo del Emisor).
6. Invocacion a todos Eventos de la SET (Cancelacion, inutilizacion, etc.)
7. Consulta de RUC.

## Para quien esta pensado FacturApi

**FacturApi** esta pensado para los **integradores** o implementadores de Sistemas, desarrolladores o empresas de software que no quieren cargar con el trabajo de 6+ meses para desarrollar un nuevo proyecto de software integrado para facturar desde su Sistema, y que desean imprimir documentos electronicos desde sus sistemas existentes.

FacturApi tambien es utilizado por los equipos internos de desarrollo de empresas, o departamento de informatica de cualquier organizacion que ya posea un sistema y que requiera emitir documentos electronicos en los proximos dias.

Finalmente FacturApi tambien puede ser utilizado por proveedores de software renombrados del exterior que tienen clientes en el Pais y desean incorporar funciones de facturacion electronicas en sus aplicaciones, para el cual brindamos todo el soporte tecnico y el acceso para poder crear documentos electronicos.


## Funciones de FacturApi

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

