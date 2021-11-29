---
title: Referencia de la API - FacturAPI

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  - <a href='#'>FacturApi Login</a>
  - <a href='https://www.facturasend.com.py'>Inicio de FacturApi</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentacion de FacturApi
---

# Introduccion
Bienvenido a la documentacion de referencia de **FacturApi**. La API paraguaya de Facturacion Electronica con el cual podras implementar rapidamente la integracion de tu software con la SET para generar, validar, firmar e imprimir documentos electronicos para tu Empresa o tus Clientes.

La API esta desarrollada con una plataforma que brinda seguridad de autenticacion y autorizacion, permitiendo el acceso a recursos, siguiendo los estandares recomendados y utilizando Single Sign On para el acceso a la Aplicacion Web, no almacenando contrasenas del password y utilizando tokens de actualizacion para evitar acceso no autorizado y clasificando los datos en ambientes diferentes para cada cliente.

## Que es FacturApi 
**FacturApi** es una plataforma compuesta de una Aplicacion Web que actua como una consola o panel de control para configurar los datos del contribuyente, visualizar los documentos generados, invocar los eventos de la SET y obtener diferentes tipos de reportes y graficos.

**FacturApi** tambien esta compuesto de una capa de nivel de nivel de servicios web que permite al integrador poder invocar las funciones mediante llamadas a la API REST, lo cual facilita la integracion de cualquier Sistema o Aplicativo ya desarrollado sea este Escritorio, Web o movil con el fin de emitir documentos electronicos (Facturas, Autofacturas, Notas de Debitos y Creditos y Notas de retencion electronicas), validados por la SET y realizar todas las operaciones vinculadas con la Facturacion Electronica (Sifen).

Con FacturApi podras crear varias empresas cada una de ellas para cada uno de los clientes especificos que posees, manteniendo un control sencillo e independiente de los datos e invitando a usuarios con diferentes roles para acceder de forma controlada a los recursos. 

FacturApi contempla todos los procesos requeridos para la generacion de documentos electronicos.

1. Generacion del Documento XML segun el manual tecnico de la SET
2. Firma del Documento Electronico, utilizando el certificado digital de la Empresa contribuyente
3. Generacion del Codigo QR para la Factura.
4. Comunicacion con la SET (Envio de documentos electronicos, generacion de lotes de envio, consulta de documentos.)
5. Generacion del Documento KUDE (Archivo PDF de la Factura o Documento electronico, personalizado de acuerdo al Logo del Emisor).
6. Envio de email del documento electronico al contribuyente receptor.
7. Invocacion a todos Eventos de la SET (Cancelacion, inutilizacion, etc.)
8. Consulta de RUC.

## Para quien fue pensado FacturApi

**FacturApi** fue pensado para los **integradores** o **implementadores** de Sistemas, desarrolladores o empresas de software que aun no estan capacitados sobre el Sifen o que desean evitarse la carga de trabajo para analizar, disenar y proyectar, desarrollar e implantar un nuevo proyecto de software integrado para facturar electronicamente desde su Sistema, y que desean imprimir documentos electronicos desde sus sistemas existentes de forma sencilla, rapida sin mucha codificacion ni complicacion.

FacturApi tambien es utilizado por los equipos internos de desarrollo de empresas, o departamento de informatica de cualquier organizacion que ya posea un sistema y que requiera emitir documentos electronicos en los proximos dias.

Finalmente FacturApi tambien puede ser utilizado por proveedores de software renombrados del exterior que tienen clientes en el Pais y desean incorporar funciones de facturacion electronicas en sus aplicaciones, para el cual brindamos todo el soporte tecnico y el acceso para poder crear documentos electronicos.

FacturApi no fue pensado para los duenos de empresa, empresarios o emprendedores, o los negocios directamente, pero si desea implementar facturacion electronica en su negocio, le podemos recomendar uno de nuestros aliados o parters que ya tienen integrado su sistema con FacturAPI.

## Como empiezo a generar Documentos Electronicos

El camino normal para generar documentos electronicos y realizar todos los procesos involucrados con la SET es obtener un timbrado de prueba y una habilitacion de acceso para el uso del Sifen del ambiente de test, ademas de un certificado digital para firmar los documentos, si, incluso en ambiente de Test. Luego de esa primera condicion se debe realizar la integracion de tu sistema y validar una bateria de test de todas las funcionalidades solicitadas por la SET, se libera el ambiente a produccion y ya se pueden emitir documentos tributarios electronicos reales y validos.

Si bien este es el camino obligado, el proceso de incluirte como empresa habilitada o a tus clientes en ambiente de test puede demorar un tiempo.

Para evitar esa espera con FacturApi puedes empezar a integrar tu sistema hoy mismo y emitir tus documentos electronicos de test rapidamente validando de forma temprana tu sistema o aplicacion, no necesitas ser un contribuyente habilitado por la SET ni poseer un Certificado Digital para empezar emitir comprobantes electronicos desde nuestra Api, no te preocupes por eso, trabajaras en un ambiente desconectado de la SET pero simularas todos los mismos procesos como si ya estuvieras habilitado utilizando un certificado digital de prueba para firmar los documentos.

Los documentos electronicos emitidos en ambiente desconectados desde FacturApi, no tienen validez tributaria, y el PDF del KUDE impreso llevara la leyenda "Generado desde un Ambiente no conectado a la SET", por eso recomendamos que apenas inicies la integracion de tu sistema con FacturAPI inicies el proceso de solicitar la inclusion de tu empresa o la de tus clientes para emitir documentos electronicos en la SET.

## Cuanto cuesta el Servicio
FacturApi no tiene costo de adhesion, puedes empezar a utilizarlo inmediatamente sin pagar nada, ya que en un primer momento tendras acceso a un ambiente "No conectado a la SET" donde podras realizar todos los pasos para integrar tu sistema conforme la API Rest descrita mas abajo, enviando y recibiendo objetos JSON. 

Desde un primer momento tendras acceso a todas las funcionalidades de la aplicacion, podras ver e imprimir el PDF del Documento Electronico (KUDE) y tus Documentos Electronicos firmados con el certificado digital de prueba (XML) se guardaran en un lugar seguro en la nube por 5 anos, no pagaras nada en absoluto hasta este punto.

Luego que hayas realizado toda tu integracion y hayas obtenido tu empresa o la empresa de tu cliente la habilitacion como Facturador electronico por parte de la SET, pasaras a un ambiente de test, a travez de una opcion que podras cambiarla tu mismo dentro de la Consola.

En el ambiente conectado de test, tus documentos ya se envian a la SET, y se obtienen las respuestas de esos envios corespondientes, alli podras seguir imprimiendo unos cuantos documentos ya con tu sistema integrado mientras que FacturApi ira recolectando dicha informacion para remirirla en formato resumido posteriormente, pues la SET te pedira dicha informacion. Aun ya estando en ambiente conectado no tendras que pagar nada a FacturAPI, pues los documentos electronicos creados en esta instancia aun no son documentos electronicos reales validos.

Empezaras a abonar por el uso del servicio y de la API cuando hayas creado tu primero documento electronico en ambiente de produccion de la SET.


## Pasos para utilizar FacturApi

, de hecho eso es una de las razones por la cual muchas empresas no pueden 
Puedes iniciar la prueba con FacturApi directamente y registrandote tu mismo en https://www.facturasend.com.py, no necesitas 

# Test de FacturApi

Un buen inicio para empezar puede ser verificar la comunicacion con FacturAPI. 

Para simplemente probar la comunicacion y ver si todo funciona de forma general, ejecutae la invocacion de la capa de nivel de servicio como se muestra a la derecha.

> Para simplemente probar la comunicacion:

```shell
# Verificando si facturapi responde a la peticion
curl "https://api.facturasend.com.py/test"  
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

axios.get(`https://api.facturasend.com.py/test`).then( respuesta => {
  console.log(respuesta);
});
```

> Si todo sale bien, vera en pantalla:

```json
FacturAPI funciona.
```

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

# Lotes

## Envio de lotes
Esta invocación, crea los documentos electrónicos y los envía a la SET.

### HTTP Request

`POST http://api.facturasend.com.py/<tokenId>/lote/create`

Esta invocación, crea los documentos electrónicos y los envía a la SET.

```shell
curl "http://api.facturasend.com.py/<tokenId>/lote/create" \
  -H "Authorization: meowmeowmeow"
```

```javascript
import axios from 'axios';

axios.get(`https://api.facturasend.com.py/<tokenId>/lote`).then( respuesta => {
  console.log(respuesta);
});
```

> El comando de arriba, retornará lo siguiente:

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

Primeramente se generaran los documentos electrónicos en FacturaSend, luego se intentarán enviar a la SET.

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

