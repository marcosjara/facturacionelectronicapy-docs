---
title: Referencia de la API - FacturaSend

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  - <a href='https://console.facturasend.com.py'>Consola de FacturaSend</a>
  - <a href='https://www.facturasend.com.py'>Inicio de FacturaSend</a>

includes:

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentación de FacturaSend
---

# Introducción
Bienvenido a la documentación de **FacturaSend**. 

La **API paraguaya** de Facturación Electrónica con el cual podrás implementar rapidamente la `integración` de tu software con la SET (Subsecretaría de Estado de Tributación) para generar, validar, firmar y enviar archivos XML de documentos electrónicos y generar el PDF KUDE para tu Empresa o tus Clientes.

## Componentes de FacturaSend 
**FacturaSend** es una plataforma compuesta de una Aplicación Web que actua como una **consola** o **panel de control** para configurar los datos del contribuyente, visualizar los documentos generados, invocar los eventos de la SET y obtener diferentes tipos de reportes y gráficos.

**FacturaSend** tambien esta compuesto de una **capa de nivel de servicios** que permite al integrador poder invocar las funciones mediante llamadas a la API REST, lo cual facilita la integración de cualquier Sistema o Aplicativo ya desarrollado sea este Escritorio, Web o móvil con el fin de emitir documentos electrónicos (Facturas, Autofacturas, Notas de Débitos y Créditos y Notas de retención electrónicas) validados por la SET y el poder realizar todas las operaciones vinculadas con la Facturacion Electronica (Sifen) como por ejemplo la invocación de eventos de cancelación o inutilización de documentos.

Con **FacturaSend** podrás administrar varias empresas cada una de ellas para cada uno de los clientes especifícos que posees, manteniendo un control sencillo e independiente de los datos e invitando a otros usuarios con diferentes roles para acceder de forma controlada a los recursos, por ejemplo, puedes brindar el acceso al Contador, para visualizar los datos de su propio entorno, visualizando solamente los datos de la o las empresas asignadas.

**FacturaSend** contempla todos los procesos requeridos para la generación de documentos electrónicos, como ser:

1. Generación del documento XML segín el manual técnico de la SET.
2. Firma del documento XML, utilizando el certificado digital de la Empresa contribuyente.
3. Generación de la URL del Código QR dentro del documento XML.
4. Comunicación con la SET (Envío de documentos XML, generación de lotes de envio, consulta de documentos, etc.)
5. Generacion del Documento KUDE (Archivo PDF de la Factura o Documento electronico, personalizado de acuerdo al Logo del Emisor).
6. Envío de email del documento electrónico al contribuyente receptor.
7. Invocación de eventos de la SET (Cancelación, inutilización, etc.)
8. Consulta de RUC.

Para encontrar más información en el [Manual Técnico PDF de la SET](https://ekuatia.set.gov.py/portal/ekuatia/detail?content-id=/repository/collaboration/sites/ekuatia/documents/documentacion/documentacion-tecnica/Manual%20T%C3%A9cnico%20Versi%C3%B3n%20150.pdf) y en el [Portal de eKuatia](https://ekuatia.set.gov.py/portal/ekuatia/).

## Para quien fue pensado FacturaSend

**FacturaSend** fue pensado para los **integradores** o **implementadores** de Sistemas, **desarrolladores** o **empresas de software** que deseen evitar la complejidad de la Arquitectura de Software del Sifen no dejando de lado la implementación en sus aplicaciones y ofreciendo de igual forma ese servicio a sus clientes desde sus propios sistemas. 

También para aquellos que desean evitarse la carga de trabajo pesada de analizar, diseñar, proyectar, desarrollar e implantar en producción un nuevo proyecto de software para contados clientes, por la escasa compensación en que resulta, pero que desean que los documentos electrónicos se generen desde sus sistemas de forma transparente para el Cliente final.

FacturaSend tambien fue pensado para los **equipos internos de desarrollo** de las empresas, o **departamentos de informática** de las organizaciones que ya posen un sistema y que requiera emitir documentos electrónicos.

Finalmente FacturaSend tambien puede ser utilizado por **proveedores de software** renombrados del exterior que tienen clientes en el País y desean incorporar funciones de facturación electrónicas en sus aplicaciones, para lo cual brindamos todo el soporte técnico y el acceso a la plataforma para poder crear documentos electrónicos.

`Nota` FacturaSend realmente no fue pensado para los dueños de empresa, empresarios, emprendedores o los negocios directamente ya que FacturaSend no se trata de un sistema de ventas o control de inventario, pero si desea implementar facturación electrónica en su negocio y aun no posee un software le podemos recomendar uno de nuestros parters que ya tienen integrado su sistema con FacturaSend.

## Seguridad
**FacturaSend** utiliza `protocolos` con **altos niveles de seguridad** para la `autenticación` y `autorización` de los usuarios, permitiendo el acceso específico a los recursos de la API y utilizando **Single Sign On (SSO)** y **oAuth** para el acceso a la Aplicacion Web no almacenando contraseñas y utilizando **tokens de actualizacion** de `corto tiempo` para evitar acceso no autorizado por ataques de fuerza bruta y   **virtualizando** de forma independiente los datos para cada empresa o cliente.

Ofrecemos **trazabilidad* sobre todas las operaciones realizadas, cambios en la eliminación de datos que puedan ser realizados, donde el administrador puede visualizar todos los eventos mediante un log.

Brindamos **confidencialidad** de los datos almacenados, mediante un **contrato** no obligatorio que puede ser firmado para generar una mayor **confianza** una vez que los documentos electrónicos emitidos sean reales y válidos, es decir al pasar al ambiente de producción de la SET.

## Como empiezo a generar Documentos Electrónicos

El **proceso** normal para generar documentos electrónicos y realizar todos los eventos involucrados con la SET es **obtener un timbrado de prueba** y una **habilitacion de acceso** para el uso del SIFEN del ambiente de test, ademas de un **certificado digital** para `firmar` los documentos, si, incluso en ambiente de Test. Luego de esa primera condicion se debe realizar la **integracion de tu sistema** y validar una bateria de test de todas las funcionalidades solicitadas por la SET, se libera el ambiente a produccion y ya se pueden emitir documentos tributarios electronicos reales y validos.

Si bien este es el camino establecido por ahora, el proceso de **incluirte** como **empresa habilitada** o a tus clientes en ambiente de test puede **demorar** un tiempo.

Para evitar esa espera, con **FacturaSend** puedes empezar a integrar tu sistema hoy mismo y emitir tus documentos electronicos de test rapidamente validando de forma temprana tu sistema o aplicacion, **no necesitas** ser un contribuyente **habilitado** por la SET para ser facturador electrónico ni poseer un Certificado Digital para empezar emitir comprobantes electrónicos desde nuestra API, no te preocupes por eso, trabajarás en un ambiente desconectado de la SET pero simularás todos los mismos procesos como si ya estuvieras habilitado utilizando un **certificado digital de prueba** para firmar los documentos.

Los documentos electrónicos emitidos en ambiente desconectado desde FacturaSend no tienen validez tributaria, y el **PDF** del **KUDE** impreso llevara la leyenda `Generado desde un Ambiente no conectado a la SET`, por eso recomendamos que apenas inicies la **integracion de tu sistema** con FacturaSend inicies el proceso de solicitar la inclusion de tu empresa o la de tus clientes para emitir documentos electronicos en la SET.

## Versiones de FacturaSend
**FacturaSend** cuenta con **2 versiones** siendo la primera la versión **on-line**, que permite la integración temprana de tu aplicación pudiendo empezar a generar documentos de prueba sin ningun costo.

Si desea mayor privacidad, la versión de **FacturaSend Empresarial**, permite a las empresas contar con toda la infraestructura desarrollada dentro de los propios **servidores privados** de la empresa sean estos en una **red interna** o en la **nube**, para lo cual brindamos todo el apoyo logístico para el proceso de puesta en marcha del servicio.

### Cuanto cuesta el Servicio
En su **versión on-line**, facturaSend tiene un costo que depende de la **cantidad de documentos electrónicos generados** por epresea, podrá encontrar ésta información en la sección **Precios** del Sitio Web.

En su **versión empresarial**, tiene un costo que depende del **tiempo** y **periodo** de implementación, así como la cantidad de recursos necesarios, puede ponerse en contacto con nostros para una cotización acorde a su empresa.

### Cuando empiezo a pagar por el Servicio
Parar la versión **on-line** FacturaSend no tiene costo de adhesión, puedes empezar a utilizarlo inmediatamente sin pagar nada, ya que en un primer momento tendrás acceso a un ambiente **"No conectado a la SET"** donde podrás realizar todos los pasos para integrar tu sistema conforme la API REST descrita mas abajo, enviando y recibiendo objetos JSON. 

Al empezar tendrás acceso a **todas** las **funcionalidades** de la aplicacion, podras **ver** e **imprimir** el PDF del Documento Electrónico **(KUDE)** y tus Documentos Electrónicos **firmados** con el certificado digital de prueba (XML) se **guardaran** en un lugar seguro en la nube por 5 años, no pagarás nada en absoluto hasta este punto.

Luego que hayas **realizado** toda tu **integración** y hayas obtenido tu empresa o la empresa de tu cliente la **habilitación** como facturador electrónico por parte de la SET, pasarás a un ambiente conectado de test, a través de una opción que podrás cambiarlo desde la Consola.

En el **ambiente conectado a la SET de test**, tus documentos ya se envían a la SET, y se obtienen las respuestas de esos envíos corespondientes, allí podrás seguir generando más documentos electrónicos ya con tu sistema integrado mientras que **FacturaSend** irá recolectando dicha información para remitirla en formato resumido posteriormente, pues la SET te pedirá dicha información. Aún ya estando en ambiente conectado **no tendrás** que **abonar** nada a FacturaSend, pues los documentos electrónicos creados en esta instancia aun no son documentos electrónicos reales validos.

Empezarás a **abonar por el uso del servicio** y de la API cuando hayas creado tu primer documento electrónico en **ambiente de producción de la SET**.

## Pasos para utilizar FacturaSend

Empeza a utilizar **FacturaSend** es muy fácil.

1. Puedes iniciar registrandote tu mismo en https://www.facturaSend.com.py
2. Luego de loguearte a al aplicación, crea tu primera empresa.
3. Completa los datos fiscales de la empresa que va emitir documentos electrónicos
4. Carga un logotipo para la cabecera de la Factura (KUDE).
5. Genera y guarda la API KEY que utilizarás para conectarte vía REST API
6. Invoca a los diferentes métodos de la API REST que están descritas más abajo.
7. Visualiza los documentos electrónicos generados XML y KUDE.

# Test de FacturaSend

Un buen inicio para empezar la integración de tu sistema puede ser verificar la comunicación con FacturaSend. 

Para simplemente probar la comunicación y ver si todo funciona de forma general, ejecuta la invocación de la capa de nivel de servicio como se muestra a la derecha.

> Para simplemente probar la comunicacion:

```shell
# Verificando si FacturaSend responde a la petición
curl "https://api.facturasend.com.py/test"  
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

axios.get(`https://api.facturasend.com.py/test`)
.then( respuesta => {
  console.log(respuesta);
});
```

> Si todo sale bien, verá en pantalla:

```json
FacturaSend funciona.
```

# Autorización

Para autorizar el uso de la API cuando se hacen invocaciones al servicio, se requiere que se envíe la API KEY en el encabezado (header) de la petición

> Ejemplo para obtener autorización de los servicios:

```shell
# Basta con pasar el encabezado correcto en cada petición
curl "https://api.facturasend.com.py/<tenantId>/test" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>"
```

```javascript
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

axios.get(`https://api.facturasend.com.py/<tenantId>/test`, 
  {headers}
).then( respuesta => {
  console.log(respuesta);
});
```

> Asegurese de reemplazar `<hdiweuw-92jwwle...>` con la API key y el `<tenantId>` de la URL según lo que se proporciona en la Consola de Administración.

FacturaSend utiliza una API KEY para tener autorización a los servicios de la API. Para ello debes primeramente registrarte en la Consola con tus datos y añadir los datos de tu empresa en [Consola de Administración](https://www.facturasend.com.py).

**FacturaSend** espera que se incluya la **API key** con la clave `Authorization`, en el siguiente formato:

`Authorization: Bearer api_key_<hdiweuw-92jwwle...>`

<aside class="notice">
Debes reemplazar <code>&lt;hdiweuw-92jwwle...&gt;</code> con la API key específica de la Empresa.
</aside>

# Servicios del DE
A continuación se detallan los servicios que pueden ser realizados desde FacturaSend sobre los DEs (Documentos Electrónicos) así como también servicios adicionales que provee el SIFEN, como lo es la consulta de RUC

## Creación de un DE
```shell
curl \  
  -X \
  POST "http://api.facturasend.com.py/<tenantId>/de/create" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>" \
  -H 'Content-Type: application/json; charset=utf-8' \
  --data-raw '{
    "tipoDocumento" : 1,
    "establecimiento" : 1,
    "punto" : "001",
    "numero" : 5, 
    "descripcion" : "Aparece en el documento",
    "observacion" : "Cualquier informacion de marketing, publicidad, promociones, sorteos, etc. para el receptor",
    "fecha" : "2021-10-19T10:11:00",
    "tipoEmision" : 1,
    "tipoTransaccion" : 1,
    "tipoImpuesto" : 1,
    "moneda" : "PYG",
    "cliente" : {
        "contribuyente" : true,
        "ruc" : "2005001-1",
        "razonSocial" : "Marcos Adrian Jara Rodriguez",
        "nombreFantasia" : "Marcos Adrian Jara Rodriguez",
        "tipoOperacion" : 1,
        "direccion" : "Avda Calle Segunda y Proyectada",
        "numeroCasa" : "1515",
        "departamento" : 11,
        "departamentoDescripcion" : "ALTO PARANA",
        "distrito" : 143,
        "distritoDescripcion" : "DOMINGO MARTINEZ DE IRALA",
        "ciudad" : 3344,
        "ciudadDescripcion" : "PASO ITA (INDIGENA)",
        "pais" : "PRY",
        "paisDescripcion" : "Paraguay",
        "tipoContribuyente" : 1,
        "documentoTipo" : 1,
        "documentoNumero" : "2324234",
        "telefono" : "061229382",
        "celular" : "0983123765",
        "email" : "cliente@empresa.com, cliente@personal.com",
        "codigo" : "1548"
    },
    "usuario" : {
        "documentoTipo" : 1,
        "documentoNumero" : "157264",
        "nombre" : "Marcos Jara",
        "cargo" : "Vendedor"
    },
    "factura" : {
        "presencia" : 1
    },
    "condicion" : {
        "tipo" : 1,
        "entregas" : [{ 
            "tipo" : 1,
            "monto" : "150000",
            "moneda" : "PYG",
            "monedaDescripcion" : "Guarani",
            "cambio" : 0.0
        }, { 
            "tipo" : 3,
            "monto" : "150000",
            "moneda" : "PYG",
            "monedaDescripcion" : "Guarani",
            "cambio" : 0.0,
            "infoTarjeta" : {
                "numero" : 1234,
                "tipo" : 1,
                "tipoDescripcion" : "Dinelco",
                "titular" : "Marcos Jara",
                "ruc" : "69695654-1",
                "razonSocial" : "Bancard",
                "medioPago" : 1,
                "codigoAutorizacion" : 232524234
            }
        }, { 
            "tipo" : 2,
            "monto" : "150000",
            "moneda" : "PYG",
            "monedaDescripcion" : "Guarani",
            "cambio" : 0.0,
            "infoCheque" : {
                "numeroCheque": "32323232",
                "banco" : "Sudameris"
            }
        }],
        "credito" : {
            "tipo" : 1,
            "plazo" : "30 días",
            "cuotas" : 2,
            "montoEntrega" : 1500000.00,
            "infoCuotas" : [{
                "moneda" : "PYG",
                "monto" : 800000.00,
                "vencimiento" : "2021-10-30"
            }, {
                "moneda" : "PYG",
                "monto" : 800000.00,
                "vencimiento" : "2021-11-30"
            }]
        }
    },
    "items" : [{
        "codigo" : "A-001",
        "descripcion": "Producto o Servicio", 
        "observacion": "Información adicional o complementaria sobre el producto", 
        "ncm": "123456",
        "unidadMedida": 77,
        "cantidad": 10.5,
        "precioUnitario": 10800,
        "cambio": 0.0,
        "ivaTipo" : 1,
        "ivaBase" : 100,
        "iva" : 5,
        "lote" : "A-001",
        "vencimiento" : "2022-10-30",
        "numeroSerie" : "",
        "numeroPedido" : "",
        "numeroSeguimiento" : ""
    }]
  }'

```

```javascript
import axios from 'axios';
const data = {
  "tipoDocumento" : 1,
  "establecimiento" : 1,
  "punto" : "001",
  "numero" : 5, 
  "descripcion" : "Aparece en el documento",
  "observacion" : "Cualquier informacion de marketing, publicidad, promociones, sorteos, etc. para el receptor",
  "fecha" : "2021-10-19T10:11:00",
  "tipoEmision" : 1,
  "tipoTransaccion" : 1,
  "tipoImpuesto" : 1,
  "moneda" : "PYG",
  "cliente" : {
      "contribuyente" : true,
      "ruc" : "2005001-1",
      "razonSocial" : "Marcos Adrian Jara Rodriguez",
      "nombreFantasia" : "Marcos Adrian Jara Rodriguez",
      "tipoOperacion" : 1,
      "direccion" : "Avda Calle Segunda y Proyectada",
      "numeroCasa" : "1515",
      "departamento" : 11,
      "departamentoDescripcion" : "ALTO PARANA",
      "distrito" : 143,
      "distritoDescripcion" : "DOMINGO MARTINEZ DE IRALA",
      "ciudad" : 3344,
      "ciudadDescripcion" : "PASO ITA (INDIGENA)",
      "pais" : "PRY",
      "paisDescripcion" : "Paraguay",
      "tipoContribuyente" : 1,
      "documentoTipo" : 1,
      "documentoNumero" : "2324234",
      "telefono" : "061229382",
      "celular" : "0983123765",
      "email" : "cliente@empresa.com, cliente@personal.com",
      "codigo" : "1548"
  },
  "usuario" : {
      "documentoTipo" : 1,
      "documentoNumero" : "157264",
      "nombre" : "Marcos Jara",
      "cargo" : "Vendedor"
  },
  "factura" : {
      "presencia" : 1
  },
  "condicion" : {
      "tipo" : 1,
      "entregas" : [{ 
          "tipo" : 1,
          "monto" : "150000",
          "moneda" : "PYG",
          "monedaDescripcion" : "Guarani",
          "cambio" : 0.0
      }, { 
          "tipo" : 3,
          "monto" : "150000",
          "moneda" : "PYG",
          "monedaDescripcion" : "Guarani",
          "cambio" : 0.0,
          "infoTarjeta" : {
              "numero" : 1234,
              "tipo" : 1,
              "tipoDescripcion" : "Dinelco",
              "titular" : "Marcos Jara",
              "ruc" : "69695654-1",
              "razonSocial" : "Bancard",
              "medioPago" : 1,
              "codigoAutorizacion" : 232524234
          }
      }, { 
          "tipo" : 2,
          "monto" : "150000",
          "moneda" : "PYG",
          "monedaDescripcion" : "Guarani",
          "cambio" : 0.0,
          "infoCheque" : {
              "numeroCheque": "32323232",
              "banco" : "Sudameris"
          }
      }],
      "credito" : {
          "tipo" : 1,
          "plazo" : "30 días",
          "cuotas" : 2,
          "montoEntrega" : 1500000.00,
          "infoCuotas" : [{
              "moneda" : "PYG",
              "monto" : 800000.00,
              "vencimiento" : "2021-10-30"
          }, {
              "moneda" : "PYG",
              "monto" : 800000.00,
              "vencimiento" : "2021-11-30"
          }]
      }
  },
  "items" : [{
      "codigo" : "A-001",
      "descripcion": "Producto o Servicio", 
      "observacion": "Información adicional o complementaria sobre el producto", 
      "ncm": "123456",
      "unidadMedida": 77,
      "cantidad": 10.5,
      "precioUnitario": 10800,
      "cambio": 0.0,
      "ivaTipo" : 1,
      "ivaBase" : 100,
      "iva" : 5,
      "lote" : "A-001",
      "vencimiento" : "2022-10-30",
      "numeroSerie" : "",
      "numeroPedido" : "",
      "numeroSeguimiento" : ""
  }]
};
const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

axios.post(`https://api.facturasend.com.py/<tenantId>/de/create`, 
  data, 
  {headers})
.then( respuesta => {
  console.log(respuesta);
});
```

> El comando de arriba, retornará lo siguiente:

```json
{ 
  "success" : true,
  "deList" : [{
    "cdc": "01800695631001002100694612021112410311184194",
    "numero": "001-001-0000001",
    "estado": "Aprobado",
    "respuesta_codigo": "",
    "respuesta_mensaje": ""
  }]
}
```

Esta invocación, crea un documento electrónico y lo envía de forma síncrona a la SET, sólo es posible enviar el dato de 1 (un) Documento Electrónico por vez.

Se denomina proceso síncrono, cuando la SET valida e informa de forma inmediata la aprobación del documento electrónico, o el rechazo.

Mediante el proceso síncrono es posible conocer en línea si el Documento Electrónico fue aprobado o rechazado por algún error y saber qué error es para poder corregirlo, gracias a la respuesta del servicio.

El documento electrónico enviado con ésta peticion puede ser visualizado en la consola de FacturaSend.

<aside class="notice">
El servicio sincrono sólo está disponible en ambiente TEST de eKuatia, no así en producción.
</aside>

### Petición HTTP

`POST http://api.facturasend.com.py/<tenantId>/de/create`

### Parámetros

Los parámetros se envían en formato JSON. 

Para detalles de la estructura completa de atributos JSON que puede ser enviado como parámetro consulte la sección [Parámetros del Objeto Principal](#parametros-de-creacion-de-un-de)

Debe tener en cuenta que para éste servicio en particular debe enviar el JSON en formato de un solo objeto, sin los corchetes [].

### Respuesta
La respuesta obtenida luego de llamar a éste servicio se describe en la sección [Respuesta de Creación de un DE](#respuesta-de-creacion-de-un-de)

### Recomendaciones
Se recomienda almacenar el identificador único del Documento electrónico o CDC (Código de Control) en su sistema, junto con la operación o movimiento que generó el Comprobante, ya sea que éste haya sido una Compra, Venta, Cobro, Pago, etc. 

El valor de éste CDC será muy útil más adelante, cuando desee obtener una copia del XML del Documento o incluso si desea obtener el PDF KUDE para imprimirlo desde su aplicación. Otras operaciones importantes que podrá realizar son la de Cancelar el Documento Electrónico o informara a la SET sobre otros eventos.

### Validaciones
FacturaSend realizará las validaciones de los valores de los atributos, conforme las especificaciones del manual técnico, antes de enviar a la SET, retornando el mensaje de error en la respuesta de invocación de éste servicio.

## Creación de varios DEs 

```shell
curl \
  -X \
  POST "http://api.facturasend.com.py/<tenantId>/lote/create" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>"
  -H 'Content-Type: application/json; charset=utf-8' \
  --data-raw '[{
  "tipoDocumento" : 1,
  "establecimiento" : 1,
  "punto" : "001",
  "numero" : 5, 
  "descripcion" : "Aparece en el documento",
  "observacion" : "Cualquier informacion de marketing, publicidad, promociones, sorteos, etc. para el receptor",
  "fecha" : "2021-10-19T10:11:00",
  "tipoEmision" : 1,
  "tipoTransaccion" : 1,
  "tipoImpuesto" : 1,
  "moneda" : "PYG",
  "cliente" : {
      "contribuyente" : true,
      "ruc" : "2005001-1",
      "razonSocial" : "Marcos Adrian Jara Rodriguez",
      "nombreFantasia" : "Marcos Adrian Jara Rodriguez",
      "tipoOperacion" : 1,
      "direccion" : "Avda Calle Segunda y Proyectada",
      "numeroCasa" : "1515",
      "departamento" : 11,
      "departamentoDescripcion" : "ALTO PARANA",
      "distrito" : 143,
      "distritoDescripcion" : "DOMINGO MARTINEZ DE IRALA",
      "ciudad" : 3344,
      "ciudadDescripcion" : "PASO ITA (INDIGENA)",
      "pais" : "PRY",
      "paisDescripcion" : "Paraguay",
      "tipoContribuyente" : 1,
      "documentoTipo" : 1,
      "documentoNumero" : "2324234",
      "telefono" : "061229382",
      "celular" : "0983123765",
      "email" : "cliente@empresa.com, cliente@personal.com",
      "codigo" : "1548"
  },
  "usuario" : {
      "documentoTipo" : 1,
      "documentoNumero" : "157264",
      "nombre" : "Marcos Jara",
      "cargo" : "Vendedor"
  },
  "factura" : {
      "presencia" : 1
  },
  "condicion" : {
      "tipo" : 1,
      "entregas" : [{ 
          "tipo" : 1,
          "monto" : "150000",
          "moneda" : "PYG",
          "monedaDescripcion" : "Guarani",
          "cambio" : 0.0
      }, { 
          "tipo" : 3,
          "monto" : "150000",
          "moneda" : "PYG",
          "monedaDescripcion" : "Guarani",
          "cambio" : 0.0,
          "infoTarjeta" : {
              "numero" : 1234,
              "tipo" : 1,
              "tipoDescripcion" : "Dinelco",
              "titular" : "Marcos Jara",
              "ruc" : "69695654-1",
              "razonSocial" : "Bancard",
              "medioPago" : 1,
              "codigoAutorizacion" : 232524234
          }
      }, { 
          "tipo" : 2,
          "monto" : "150000",
          "moneda" : "PYG",
          "monedaDescripcion" : "Guarani",
          "cambio" : 0.0,
          "infoCheque" : {
              "numeroCheque": "32323232",
              "banco" : "Sudameris"
          }
      }],
      "credito" : {
          "tipo" : 1,
          "plazo" : "30 días",
          "cuotas" : 2,
          "montoEntrega" : 1500000.00,
          "infoCuotas" : [{
              "moneda" : "PYG",
              "monto" : 800000.00,
              "vencimiento" : "2021-10-30"
          }, {
              "moneda" : "PYG",
              "monto" : 800000.00,
              "vencimiento" : "2021-11-30"
          }]
      }
  },
  "items" : [{
      "codigo" : "A-001",
      "descripcion": "Producto o Servicio", 
      "observacion": "Información adicional o complementaria sobre el producto", 
      "ncm": "123456",
      "unidadMedida": 77,
      "cantidad": 10.5,
      "precioUnitario": 10800,
      "cambio": 0.0,
      "ivaTipo" : 1,
      "ivaBase" : 100,
      "iva" : 5,
      "lote" : "A-001",
      "vencimiento" : "2022-10-30",
      "numeroSerie" : "",
      "numeroPedido" : "",
      "numeroSeguimiento" : ""
  }]
}]'
```

```javascript
import axios from 'axios';
const data = [{
  "tipoDocumento" : 1,
  "establecimiento" : 1,
  "punto" : "001",
  "numero" : 5, 
  "descripcion" : "Aparece en el documento",
  "observacion" : "Cualquier informacion de marketing, publicidad, promociones, sorteos, etc. para el receptor",
  "fecha" : "2021-10-19T10:11:00",
  "tipoEmision" : 1,
  "tipoTransaccion" : 1,
  "tipoImpuesto" : 1,
  "moneda" : "PYG",
  "cliente" : {
      "contribuyente" : true,
      "ruc" : "2005001-1",
      "razonSocial" : "Marcos Adrian Jara Rodriguez",
      "nombreFantasia" : "Marcos Adrian Jara Rodriguez",
      "tipoOperacion" : 1,
      "direccion" : "Avda Calle Segunda y Proyectada",
      "numeroCasa" : "1515",
      "departamento" : 11,
      "departamentoDescripcion" : "ALTO PARANA",
      "distrito" : 143,
      "distritoDescripcion" : "DOMINGO MARTINEZ DE IRALA",
      "ciudad" : 3344,
      "ciudadDescripcion" : "PASO ITA (INDIGENA)",
      "pais" : "PRY",
      "paisDescripcion" : "Paraguay",
      "tipoContribuyente" : 1,
      "documentoTipo" : 1,
      "documentoNumero" : "2324234",
      "telefono" : "061229382",
      "celular" : "0983123765",
      "email" : "cliente@empresa.com, cliente@personal.com",
      "codigo" : "1548"
  },
  "usuario" : {
      "documentoTipo" : 1,
      "documentoNumero" : "157264",
      "nombre" : "Marcos Jara",
      "cargo" : "Vendedor"
  },
  "factura" : {
      "presencia" : 1
  },
  "condicion" : {
      "tipo" : 1,
      "entregas" : [{ 
          "tipo" : 1,
          "monto" : "150000",
          "moneda" : "PYG",
          "monedaDescripcion" : "Guarani",
          "cambio" : 0.0
      }, { 
          "tipo" : 3,
          "monto" : "150000",
          "moneda" : "PYG",
          "monedaDescripcion" : "Guarani",
          "cambio" : 0.0,
          "infoTarjeta" : {
              "numero" : 1234,
              "tipo" : 1,
              "tipoDescripcion" : "Dinelco",
              "titular" : "Marcos Jara",
              "ruc" : "69695654-1",
              "razonSocial" : "Bancard",
              "medioPago" : 1,
              "codigoAutorizacion" : 232524234
          }
      }, { 
          "tipo" : 2,
          "monto" : "150000",
          "moneda" : "PYG",
          "monedaDescripcion" : "Guarani",
          "cambio" : 0.0,
          "infoCheque" : {
              "numeroCheque": "32323232",
              "banco" : "Sudameris"
          }
      }],
      "credito" : {
          "tipo" : 1,
          "plazo" : "30 días",
          "cuotas" : 2,
          "montoEntrega" : 1500000.00,
          "infoCuotas" : [{
              "moneda" : "PYG",
              "monto" : 800000.00,
              "vencimiento" : "2021-10-30"
          }, {
              "moneda" : "PYG",
              "monto" : 800000.00,
              "vencimiento" : "2021-11-30"
          }]
      }
  },
  "items" : [{
      "codigo" : "A-001",
      "descripcion": "Producto o Servicio", 
      "observacion": "Información adicional o complementaria sobre el producto", 
      "ncm": "123456",
      "unidadMedida": 77,
      "cantidad": 10.5,
      "precioUnitario": 10800,
      "cambio": 0.0,
      "ivaTipo" : 1,
      "ivaBase" : 100,
      "iva" : 5,
      "lote" : "A-001",
      "vencimiento" : "2022-10-30",
      "numeroSerie" : "",
      "numeroPedido" : "",
      "numeroSeguimiento" : ""
  }]
}];
const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

axios.post(`https://api.facturasend.com.py/<tenantId>/lote/create`, 
  data, 
  {headers}
)
.then( respuesta => {
  console.log(respuesta);
});
```

Esta invocación, crea varios documentos electrónicos (hasta un máximo de 50 del mismo tipo) y los envía a la SET utilizando el proceso por lotes o asíncrono. 

Se denomina proceso asíncrono, cuando no hay una respuesta inmediata de aprobación o rechazo desde la SET sobre los documentos enviados. Esto debe consultarse mediante otro proceso.

En éste caso NO es posible obtener en la respuesta, la información de si el Documento Electrónico fue Aprobado o Rechazado aún, pero FacturaSend se encargará de consultar esa información más tarde, invocando otro Servicio a la SET. 

Todos los documentos electrónicos enviados con ésta peticion pueden ser visualizados en la consola de FacturaSend.

### Petición HTTP

`POST http://api.facturasend.com.py/<tenantId>/lote/create`

> El comando de arriba, retornará lo siguiente:

```json
{ 
  "success" : true,
  "deList" : [{
    "cdc": "01800695631001002100694612021112410311184194",
    "numero": "001-001-0000001",
    "estado": "Aprobado",
    "respuesta_codigo": "",
    "respuesta_mensaje": ""
  }]
}
```

### Parámetros

Los parámetros del Documento Electrónico se envían en formato JSON y tienen la misma estructura que el de creación de 1 (un) sólo DE. 

Para detalles de la estructura completa de atributos JSON que puede ser enviado como parámetro consulte la sección [Parámetros del Objeto Principal](#parametros-de-creacion-de-un-de)

También se pueden especificar algunos parametros de consulta junto con la URL:
### Parámetros de Consulta (QueryParam)
Parámetro | Requerido | Descripción
--------- | --------- | -----------
draft | No | Especifique **true** para generar el documento electrónico en borrador. Un DE en borrador no se envia a la SET hasta que se cofnirma. Su valor por defecto es **false**.
xml | No | Especifique **true** para obtener en el resultado el/los XML/s generado/s en la operación. Su valor por defecto es **false**.
qr | No | Especifique **true** para obtener en el resultado el/los QR/s generado/s en la operación. Su valor por defecto es **false**.

Por ejemplo, la petición puede ser realizado de ésta manera:
POST http://api.facturasend.com.py/&lt;tenantId&gt;/lote/create?draft=true&xml=true&qr=true.

Para confirmar/descartar un borrador, vea la sección XYZ

Tenga en cuenta que a diferencia del método anterior, aqui se recibe un array de objetos, por lo cual se debe empezar el JSON con corchetes [] aunque vaya a enviar 1 (un) sólo documento. El límite de objetos es hasta 50 documentos electrónicos por cada invocación.

### Respuesta
El formato de la respuesta es igual al método anterior y se describe en la sección [Respuesta de Creación de un DE](#respuesta-de-creacion-de-un-de)

### Recomendaciones
- El implementador es libre de utilizar el método más conveniente del servicio a implementar en su sistema, sea el sincrono o el asíncrono, de todas formas dada la similitud entre ambos, se recomienda implementar los dos tipos en su sistema y parametrizar uno u otro de forma opcional, ya que a veces la SET establece que sólo pueda utilizarse el asincrono (ésto podrá cambiar más adelante.)

- Una situación que se dá con el proceso asíncrono es que como se realiza en dos tiempos, se puede entregar al Cliente, por ejemplo, una Factura Electrónica que sin nuestro conocimiento sufrió un rechazo por algún motivo y tenga que ser corregido en un paso siguiente. 
En éste caso existen técnicas que se deben manejar para no alterar el CDC (Código de Control) evitando que el Cliente tenga que devolver el Comprobante para un cambio. Además la SET brinda un plazo de 72 horas para realizar cualquier cambio o modificación sobre el comprobante.

### Validaciones

- Todos los documentos que se envían utilizando éste método, deben ser del mismo tipo, por ejemplo todos ellos factura electrónica.
- Puede enviar como mínimo 1 documento y como máximo 50 por llamada, si tienen más debe realizarlo en una siguiente llamada.

## Consulta DE por ID

> Para consultar el DE:

```shell
# Consulta de un DE por el Id de Registro de FacturaSend
curl \
  -X \
  GET "https://api.facturasend.com.py/<tenantId>/de/id/24"  
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>"
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

axios.get(`https://api.facturasend.com.py/<tenantId>/de/id/24`, 
  {headers}
)
.then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{
  "success": true,
  "result": {
    "id": 24,
    "fecha": "2022-08-11T18:49:26.840Z",
    "rde": {
      //Contenido del XML en formato JSON
    },
    "situacion": 4,
    "is_conectado": 1,
    "is_borrado": 0,
    "lote_id": 404,
    "lote_estado": 3,
    "info_codigo": "1001",
    "info_descripcion": "CDC duplicado"
  }
}
```
Este servicio consulta los datos del DE por el Id de registro de FacturaSend, recuperando informaciones importantes sobre el DE.

Este servicio es similar al servicio "Consulta DE por CDC", con la diferencia del parámetro de entrada

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**id** | **Si** | Id de Registro de FacturaSend

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | true si la consulta se ejecutó con éxito, false si dio algún error
error | string | El mensaje de error en caso de que haya retornado success=false.
result | objeto | Datos del Registro caso exista el DE, como id del registro, fecha, situacion, is_conectado, is_borrado, lote_estado, info_codigo e info_descripcion

## Consulta DE por CDC

> Para consultar el DE por el CDC:

```shell
# Consulta de un DE por el Código de Control (CDC)
curl \
  -X \
  GET "https://api.facturasend.com.py/<tenantId>/de/cdc/01800695631001001000000612021112917595714694"  
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>"
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

axios.get(`https://api.facturasend.com.py/<tenantId>/de/cdc/01800695631001001000000612021112917595714694`, 
  {headers}
)
.then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{
  "success": true,
  "result": {
    "id": 764,
    "fecha": "2022-08-11T18:49:26.840Z",
    "rde": {
      //Contenido del XML en formato JSON
    },
    "situacion": 4,
    "is_conectado": 1,
    "is_borrado": 0,
    "lote_id": 404,
    "lote_estado": 3,
    "info_codigo": "1001",
    "info_descripcion": "CDC duplicado"
  }
}
```
Este servicio consulta los datos del DE del registro de FacturaSend, recuperando informaciones importantes para el control de flujo.

Este servicio es similar al servicio "Consulta DE por ID", con la diferencia del parámetro de entrada

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**cdc** | **Si** | Código CDC de 44 dígitos del Documento Electrónico

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | true si la consulta se ejecutó con éxito, false si dio algún error
error | string | El mensaje de error en caso de que haya retornado success=false.
result | objeto | Datos del Registro caso exista el DE, como id del registro, fecha, situacion, is_conectado, is_borrado, lote_estado, info_codigo e info_descripcion

## Consulta de estados de DE(s) por CDC(s)

> Para consultar el estado del DTE:

```shell
# Consulta el estado de un DTE en base a un array de códigos de control (CDC)
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/de/estado" 
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>"
  -H 'Content-Type: application/json; charset=utf-8' \
  --data-raw '{
    cdcList : [{
        "cdc": "01800695631001001038720612021112917595714694"
    }, {
        "cdc": "01800695631001001000000612021312917595714694"
    }, {
        "cdc": "otro.."
    }]
  }'
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

const data = {
    cdcList : [{
        "cdc": "01800695631001001038720612021112917595714694"
    }, {
        "cdc": "01800695631001001000000612021312917595714694"
    }, {
        "cdc": "otro.."
    }]
};

axios.post(`https://api.facturasend.com.py/<tenantId>/de/estado`, 
  data, 
  {headers}
)
.then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{
  "success": true,
  "deList" : [{
    "cdc": "01800695631001001038720612021112917595714694",
    "numero": "001-001-0000001",
    "estado": "Aprobado",
    "situacion": 2,
    "fecha": "2022-04-02T08:56:58-04:00",
    "respuesta_codigo": "0260",
    "respuesta_mensaje": "Autorización del DE satisfactoria"
  }, {
    "cdc": "01800695631001001000000612021312917595714694",
    "numero": "001-001-0000002",
    "estado": "Aprobado",
    "situacion": 2,
    "fecha": "2022-04-02T08:56:58-04:00",
    "respuesta_codigo": "0260",
    "respuesta_mensaje": "Autorización del DE satisfactoria"
  }, {
    "cdc": "otro..",
    "numero": "001-001-0000003",
    "estado": "Aprobado",
    "situacion": 2,
    "fecha": "2022-04-02T08:56:58-04:00",
    "respuesta_codigo": "0260",
    "respuesta_mensaje": "Autorización del DE satisfactoria"
  }]
}
```
Este servicio consulta el estado de los documentos electrónicos en FacturaSend, retornando también el código de respuesta que se obtuvo desde el SIFEN, asi como también su mensaje. 

Puede utilizar éste método para consultar los estados de aquellos documentos que han sido enviados de forma asincrona y del cual no pudo conocer su situación al momento de su creación.

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**cdcList** | **Si** | Array de códigos CDC de los cuales se desea obtener el estado del Documento Electrónico<br/><br/>Los atributos de éste array se pueden encontrar en la [lista de abajo](#parametros-de-cdclist)

### Parámetros de cdcList
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**cdc** | **Si** | Código CDC de 44 dígitos del Documento Electrónico

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | true si la consulta se ejecutó con éxito, false si dio algún error
error | string | El mensaje de error en caso de que haya retornado success=false.
deList | array | El array con las respuestas de los estados de cada DE consultado cuyos campos se describen en  [esta lista](#respuesta-delist-de-consulta-de-estado)

### Respuesta deList de Consulta de Estado

Atributos | Tipo | Description
--------- | ---- | -----------
cdc | string | Id único de 44 dígitos del Documento Electrónico consultado
fecha | date-time | Fecha de Proceso en el SIFEN en formato yyyy-MM-ddThh:mm:ss
numero | string | Número de Documento Electrónico en formato 001-001-0000001
situacion | number | Situacion numerica en FacturaSend, con los posibles valores:<br>-1 = Borrador<br>0 = Generado DE<br>1 = Enviado en un Lote<br>2 = Aprobado (Caso sea sincrono es inmediato)<br>3 = Aprobado con observacion<br>4 = Rechazado<br>98 = Inexistente<br>99 = Cancelado.<br>Puede utilizar estos mismos estados en su Sistema<br>
respuesta_codigo | string | Código de la Respuesta de la SET
respuesta_mensaje | string | Mensaje de Respuesta de la SET

## Obtener XML del DE
> Para consultar el XML de un DTE:

```shell
# Consulta del XML de un DTE por el Código de Control (CDC)
curl \
  GET "https://api.facturasend.com.py/<tenantId>/de/xml/01800695631001001000000612021112917595714694?json=false"  
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>"
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};


axios({
  url: `https://api.facturasend.com.py/<tenantId>/de/xml/01800695631001001000000612021112917595714694?json=false`,
  method: 'GET',
  responseType: 'blob',
  {headers}
})
.then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```text
Retorna el Contenido del XML
```

Este servicio consulta el documento electrónico en formato de contenido XML que fue emitido desde FacturaSend con el CDC pasado como parámetro. 

No se realizan validaciones de estado, por lo cual se pueden obtener el XML de un DE aprobado como rechazado.

Recordando que el XML de un DE aprobado representa al archivo con valor fiscal y comercial almacenado en el eKuatia.

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**cdc** | **Si** | Código CDC de 44 dígitos del Documento Electrónico
json | No | Si se envia como 'true' en la queryParam (?json=true) entonces se recuperará el contenido del Archivo XML pero en formato de objeto JSON

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
main | text | Contenido del XML

## Obtener PDF del DE
> Para obtener el PDF de uno o más documentos electrónicos:

```shell
# Obtiene el documento PDF de los Códigos de Control (CDC) que se pasan como parámetro
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/de/pdf" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>" \
  --data-raw '{
    cdcList : [{
        "cdc": "01800695631001001038720612021112917595714694"
    }, {
        "cdc": "01800695631001001000000612021312917595714695"
    }, {
        "cdc": "otro.."
    }],
    "type": "base64",
    "format": "ticket"
  }'
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

const data = {
    cdcList : [{
        "cdc": "01800695631001001038720612021112917595714694"
    }, {
        "cdc": "01800695631001001000000612021312917595714695"
    }, {
        "cdc": "otro.."
    }],
    "type": "base64",
    "format": "ticket"
};

axios.post({
  url: `https://api.facturasend.com.py/<tenantId>/de/pdf`,
  method: 'POST',
  responseType: 'blob',
  {headers}
}
).then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```text
Binario o base64 del Documento PDF
```
Este servicio consulta el/los documento/s PDF KUDE de uno o más documentos electrónicos (como máximo 50) desde FacturaSend. 

En el caso de incluir más de un CDC, el sistema recuperara 1 sólo documento, pero con varias hojas, cada una de ellas conteneniendo el KUDE de los diferentes documentos electrónicos.

Este servicio no realiza validaciones de estado sobre el Documento Electronico para obtener el PDF, por lo cual debe saber que puede obtener el PDF tanto de un Documento Electrónico Aprobado como de uno Rechazado 

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**cdcList** | **Si** | Array de códigos CDC de los cuales se desea obtener el Documento PDF KUDE<br/><br/>Los atributos de éste array, son iguales a la Consulta de Estados, que se pueden encontrar en la [lista de arriba](#parametros-de-cdclist)
type | No | Tipo de información que se desea obtener<br/><br/>Por defecto el Documento se recupera en formato Binario.<br/><br/>La opción alternativa es 'base64'
format | No | Especifique el formato de impresión para el Documento Electrónico, "ticket" o "custom". Si desea obtener el PDF en el formato normal de Factura (especificado en el establecimiento) ignore ésta opción.

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
main | binary | Documento PDF en formato binary o base64

## Reenviar correo de un DE
> Para enviar un correo electrónico al receptor del DE, utilize la siguiente API:

```shell
# Re-envia el correo al receptor
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/de/email" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>" \
  --data-raw '{
    cdcList : [{
        "cdc": "01800695631001001038720612021112917595714694"
    }, {
        "cdc": "01800695631001001000000612021312917595714695"
    }, {
        "cdc": "otro.."
    }]
  }'
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

const data = {
    cdcList : [{
        "cdc": "01800695631001001038720612021112917595714694"
    }, {
        "cdc": "01800695631001001000000612021312917595714695"
    }, {
        "cdc": "otro.."
    }]
};

axios.post({
  url: `https://api.facturasend.com.py/<tenantId>/de/email`,
  method: 'POST',
  {headers}
}
).then( respuesta => {
  console.log(respuesta);
});
```

> El envio de email se ejecutará de forma asincrona

Reenvia un correo electrónico al receptor. Utilice en aquellos casos donde el correo no llego al destinatario.

No es posible cambiar la dirección de destino.

Tenga en cuenta que al Crear el DE, y si el parámetro de envio de email está activo, ya se envía el correo a los destinatarios del DE, cuyas direcciones se especificand en data.cliente.

Por lo general, el re-envio de email no es necesario, si su receptor no recibe su correo inmediatamente puede ser por el sistema de envio o servidor de correos o por que le pudo haber llegado en la carpeta SPAM.

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**cdcList** | **Si** | Array de códigos CDC de los cuales se desea enviar el email<br/><br/>

### Respuesta
Recibirá una respuesta true, inmediatamente luego de ejecutado esta API

## Parámetros de creación de un DE

> Ejemplo de Datos JSON para creación de un Documento Electrónico:

```json
{
  "tipoDocumento" : 1,
  "establecimiento" : 1,
  "punto" : "001",
  "numero" : 4, 
  "descripcion" : "Aparece en el documento",
  "observacion" : "Cualquier informacion de marketing, publicidad, promociones, sorteos, etc. para el receptor",
  "fecha" : "2021-10-19T10:11:00",
  "tipoEmision" : 1,
  "tipoTransaccion" : 1,
  "tipoImpuesto" : 1,
  "moneda" : "PYG",
  "condicionAnticipo" : null,
  "condicionTipoCambio": null,
  "cambio": 6700.0,
  "cliente" : {
      "contribuyente" : true,
      "ruc" : "2005001-1",
      "razonSocial" : "Marcos Adrian Jara Rodriguez",
      "nombreFantasia" : "Marcos Adrian Jara Rodriguez",
      "tipoOperacion" : 1,
      "direccion" : "Avda Calle Segunda y Proyectada",
      "numeroCasa" : "1515",
      "departamento" : 11,
      "distrito" : 143,
      "ciudad" : 3344,
      "pais" : "PRY",
      "tipoContribuyente" : 1,
      "documentoTipo" : 1,
      "documentoNumero" : "2324234",
      "telefono" : "061229382",
      "celular" : "0983123765",
      "email" : "cliente@empresa.com, cliente@personal.com",
      "codigo" : "1548"
  },
  "usuario" : {
      "documentoTipo" : 1,
      "documentoNumero" : "157264",
      "nombre" : "Marcos Jara",
      "cargo" : "Vendedor"
  },
  "factura" : {
      "presencia" : 1,    
      "fechaEnvio" : null,
      "dncp" : {
          "modalidad" : "ABC",
          "entidad" : 1,
          "año" : 2021,
          "secuencia" : 3377,
          "fecha" : "2020-10-14T10:11:00"
      }
  },
  "condicion" : {
      "tipo" : 1,
      "entregas" : [{ 
          "tipo" : 1,
          "monto" : "150000",
          "moneda" : "PYG",
          "cambio" : 0.0
      }, { 
          "tipo" : 3,
          "monto" : "150000",
          "moneda" : "PYG",
          "cambio" : 0.0,
          "infoTarjeta" : {
              "numero" : 1234,
              "tipo" : 1,
              "titular" : "Marcos Jara",
              "ruc" : "69695654-1",
              "razonSocial" : "Bancard",
              "medioPago" : 1,
              "codigoAutorizacion" : 232524234
          }
      }, { 
          "tipo" : 2,
          "monto" : "150000",
          "moneda" : "PYG",
          "cambio" : 0.0,
          "infoCheque" : {
              "numeroCheque": "32323232",
              "banco" : "Sudameris"
          }
      }],
      "credito" : {
          "tipo" : 1,
          "plazo" : "30 días",
          "cuotas" : 2,
          "infoCuotas" : [{
              "moneda" : "PYG",
              "monto" : 800000.00,
              "vencimiento" : "2021-10-30"
          }, {
              "moneda" : "PYG",
              "monto" : 800000.00,
              "vencimiento" : "2021-11-30"
          }]
      }
  },
  "items" : [{
      "codigo" : "A-001",
      "descripcion": "Producto o Servicio", 
      "observacion": "Información adicional o complementaria sobre el producto", 
      "partidaArancelaria" : 4444,
      "ncm": "123456",
      "unidadMedida": 77,
      "cantidad": 10.5,
      "precioUnitario": 10800,
      "cambio": 0.0,
      "descuento": 0,
      "anticipo": 0,
      "pais" : "PRY",
      "tolerancia" : 1,
      "toleranciaCantidad" : 1,
      "toleranciaPorcentaje" : 1,
      "cdcAnticipo" : "44digitos",
      "dncp" : {
          "codigoNivelGeneral" : "12345678",
          "codigoNivelEspecifico" : "1234",
          "codigoGtinProducto" : "12345678",
          "codigoNivelPaquete" : "12345678"
      },
      "ivaTipo" : 1,
      "ivaBase" : 100,
      "iva" : 5,
      "lote" : "A-001",
      "vencimiento" : "2022-10-30",
      "numeroSerie" : "",
      "numeroPedido" : "",
      "numeroSeguimiento" : "",
      "registroSenave" : "RS-0821221",
      "registroEntidadComercial" : "REC-8923/2022",
      "sectorAutomotor" : {
          "tipo" : 1,
          "chasis" : "4525234523542353245",
          "color" : "Rojo",
          "potencia" : 1500,
          "capacidadMotor" : 5,
          "capacidadPasajeros" : 5,
          "pesoBruto" : 10000,
          "pesoNeto" : 8000,
          "tipoCombustible" : 9,
          "numeroMotor" : "323234234234234234",
          "capacidadTraccion" : 151.01,
          "año" : 2009,
          "tipoVehiculo" : "Camioneta",
          "cilindradas" : "3500"
      }
  }],
  "sectorEnergiaElectrica" : {
      "numeroMedidor" : "132423424235425",
      "codigoActividad" : 12,
      "codigoCategoria" : "001",
      "lecturaAnterior" : 4,
      "lecturaActual" : 5
  },
  "sectorSeguros" : {
      "codigoAseguradora" : "112",
      "codigoPoliza" : "AAAA",
      "numeroPoliza" : "BBBB",
      "vigencia" : 1,
      "vigenciaUnidad" : "año",
      "inicioVigencia" : "2021-10-01T00:00:00",
      "finVigencia" : "2022-10-01T00:00:00",
      "codigoInternoItem" : "A-001"
  },
  "sectorSupermercados" : {
      "nombreCajero" : "Juan Antonio Caceres",
      "efectivo" : 150000,
      "vuelto" : 30000,
      "donacion" : 1000,
      "donacionDescripcion" : "Donado para la caridad"
  },
  "sectorAdicional" : {
      "ciclo" : "Mensualidad Pago",
      "inicioCiclo" : "2021-09-01",
      "finCiclo" : "2021-10-01",
      "vencimientoPago" : "2021-11-01",
      "numeroContrato" : "AF-2541",
      "saldoAnterior" : 1550000
  },
  "transporte" : {
      "tipo" : 1,
      "modalidad" : 1,
      "tipoResponsable" : 1,
      "condicionNegociacion" : "FOB",
      "numeroManifiesto" : "AF-2541",
      "numeroDespachoImportacion" : "153223232332",
      "inicioEstimadoTranslado" : "2021-11-01",
      "finEstimadoTranslado" : "2021-11-01",
      "paisDestino" : "PRY", 
      "paisDestinoNombre" : "Paraguay",
      "salida" : {
          "direccion" : "Paraguay",
          "numeroCasa" : "3232",
          "complementoDireccion1" : "Entre calle 2", 
          "complementoDireccion2" : "y Calle 7",
          "departamento" : 11,
          "distrito" : 143,
          "ciudad" : 3344,
          "pais" : "PRY",
          "telefonoContacto" : "0973987654"
      },
      "entrega" : {
          "direccion" : "Paraguay",
          "numeroCasa" : "3232",
          "complementoDireccion1" : "Entre calle 2", 
          "complementoDireccion2" : "y Calle 7",
          "departamento" : 11,
          "distrito" : 143,
          "ciudad" : 3344,
          "pais" : "PRY",
          "telefonoContacto" : "0973987654"
      },
      "vehiculo" : {
          "tipo" : "Camioneta",
          "marca" : "Nissan",
          "documentoTipo" : 1, 
          "documentoNumero" : "232323-1",
          "obs" : "",
          "numeroMatricula" : "ALTO PARANA",
          "numeroVuelo" : null
      },
      "transportista" : null
  },
  "complementarios" : {
      "ordenCompra" : 1001,
      "ordenVenta" : 1002,
      "numeroAsiento" : 1212,
      "carga" : {
          "unidadMedidaVolumenTotal" : null,
          "volumenTotal" : 10,
          "unidadMedidaPesoTotal" : null,
          "pesoTotal" : 11,
          "caracteristicaCarga" : null,
          "caracteristicaCargaDescripcion" : null
      }
  },
  "documentoAsociado" : null ,
}
```
A continuación se describe la estructura de atributos del parámetro requerido para crear un nuevo documento electrónico.

A la derecha puede observarse un ejemplo con los valores obligatorios especificados, así como la relación que guardan éstos atributos con los del manual técnico. Por ejemplo el tipo de documento en el manual técnico es el C002.

Algunos campos son obligatorios para el eKuatia, para lo cual desde FacturaSend se asumen algunos valores por defecto caso no sean proveidos en el parámetro principal.

### Parametros del objeto principal o data

Para los atributos del objeto JSON también puede utilizar **_ (underscore)**, es decir, se interpreta de la misma manera si envia *tipoDocumento* o *tipo_documento*. 

Parámetro | Requerido | Descripción
--------- | --------- | -----------
**tipoDocumento** | **Si** | Uno de los 5 tipos de documentos admitidos por eKuatia (1, 4, 5, 6, 7). Ej.:<br/>1= Factura electrónica, <br/>4= Autofactura electrónica <br/>5= Nota de crédito electrónica, <br/>6= Nota de débito electrónica, <br/>7= Nota de remisión electrónica. <br/><br/>**Campo XML:** C002.
**establecimiento**|**Si**| Representa al código de establecimiento del emisor, se puede enviar 1 o '001' <br/><br/>**Campo XML:** C005.
**punto**|**Si**| Es el punto de emisión del documento electrónico, se puede enviar 1 o '001'<br/><br/>**Campo XML:** C006.
**numero**|**Si**| Es el número del documento electrónico, se puede enviar directamente el número o completar con 0 a la izquierda hasta alcanzar 7 digitos. Ej.: 1 o '0000001'. <br/><br/>**Campo XML:**C007 
serie|No| Serie de 2 digitos de la numeración del documento electrónico. Solo debe enviarse cuando se utiliza la totalidad de la numeración de 7 dígitos, empezando por la serie AA, AB, AC, BA, BB, BC...ZZ. <br/><br/>**Campo XML:**C010 
descripcion|No| Información de interés del Fisco respecto al DE.<br/><br/>**Campo XML:** B006.
observacion|No| Información de interés del emisor respecto al DE.<br/><br/>**Campo XML:** B005.
**fecha**|**Si**| Fecha y hora de emisión del DE. <br/><br/>**Campo XML:** D002.
tipoEmision|No| Tipo de emisión del DE (1 o 2) <br/>Valores: <br/>1=Normal (Por defecto).<br/>2=Contingencia.<br/><br/>**Campo XML:** B002.
tipoTransaccion|No|Tipo de Transacción. <br/>Valores: <br/>1=Venta de mercadería (Por defecto). <br/>2=Prestación de servicios. <br/>3=Mixto (Venta de mercadería y servicios). <br/>4=Venta de activo fijo. <br/>5=Venta de divisas. <br/>6=Compra de divisas. <br/>7=Promoción o entrega de muestras. <br/>8=Donación. <br/>9=Anticipo. <br/>10=Compra de Productos. <br/>11=Venta de Crédito fiscal. <br/>12=Compra de Crédito fiscal. <br/>13=Muestras médicas (Art. 3 RG 24/2014). <br/><br/>**Campo XML:** D011.
**tipoImpuesto**|**Si**|Tipo de impuesto afectado. <br/>Valores:<br/>1=IVA.<br/>2=ISC.<br/> 3=Renta.<br/>4=Ninguno.<br/>5=IVA - Renta. <br/><br/>**Campo XML:**  D013.
moneda|No|Código de la moneda de la operación de acuerdo con la norma [ISO 4217](https://www.currency-iso.org/en/home/tables/table-a1.html). Si no se pasa asume el valor por defecto "PYG"<br/><br/>**Campo XML:**  D015.
condicionAnticipo|No|Condición del Anticipo.<br/>Valores:<br/>1=Anticipo Global. <br/>2=Anticipo por ítem.<br/>No es obligatorio informar. <br/><br/>**Campo XML:** D019.
condicionTipoCambio|No|Condición del tipo de cambio. <br/>Valores: <br/>1=Global (un solo tipo de cambio para todo el DE). <br/>2=Por ítem (tipo de cambio distinto por ítem). <br/>Obligatorio si moneda ≠ PYG, <br/>Si la moneda es PYG no enviar éste atributo o enviar con el valor null. <br/><br/>**Campo XML:** D017.
cambio|No|Valor del cambio de la moneda de la operación en la cotización del día. <br/>Ej.: 6500.00 si la moneda es USD. <br/>Si la moneda es PYG no enviar éste campo o enviar null <br/><br/>**Campo XML:** D018
cdc|No|Código CDC de 44 dígitos que desea utilizarse para el DE. <br/><br/>En ocasiones puede ser necesario re-utilizar el mismo CDC de un DE que ha sido rechazado anteriormente, por ejemplo si el Documento KUDE ya ha sido entregado al Cliente, corrigiendo el error y volviendo a intentar la aprobación con el mismo CDC.
**cliente**|**Si**|Datos del Receptor del Documento Electrónico. <br/>Ver detalle en tabla [data.cliente](#parametro-del-objeto-data-cliente).<br/>
**usuario**|**No**|Campos que identifican al responsable de la generación del DE. Ver detalle en tabla [data.usuario](#parametro-del-objeto-data-usuario).<br/>
factura|No|Conjunto de información relacionada a la Factura Electrónica. <br/>Solo es necesario cuando el tipoDocumento=1 (Factura Electrónica)<br/>Ver detalle en tabla [data.factura](#parametro-del-objeto-data-factura).<br/>
autoFactura|No|Conjunto de información relacionada a la Autofactura Electrónica<br/>Solo es necesario cuando el tipoDocumento=4 (Autofactura Electrónica<br/> Ver detalle en tabla [data.autoFactura](#parametro-del-objeto-data-autofactura).<br/>
notaCreditoDebito|No|Conjunto de información relacionada a la Nota de Credito o Debito. <br/>Solo es necesario cuando el tipoDocumento=5 o tipoDocumento=6 (Nota de Credito/Nota de Debito)<br/>Ver detalle en tabla [data.notaCreditoDebito](#parametro-del-objeto-data-notacreditodebito).<br/>
remision|No|Conjunto de información relacionada a la Remisión. <br/>Solo es necesario cuando el tipoDocumento=7 (Nota de Remisión)<br/>Ver detalle en tabla [data.remision](#parametro-del-objeto-data-remision).<br/>
**items**|**Si**|Conjunto de información relacionada a los items del Documento electrónico. <br/>Ver detalle en tabla [data.items](#parametro-del-objeto-data-items).<br/>
condicion|No|Conjunto de información relacionada a la condición de Pago por el Documento electrónico. <br/>Ver detalle en tabla [data.condicion](#parametro-del-objeto-data-condicion).<br/>
complementarios|No|Conjunto de información relacionada a los datos complementarios del Documento electrónico. <br/>Ver detalle en tabla [data.complementarios](#parametro-del-objeto-data-complementarios).<br/>
transporte|No|Conjunto de información relacionada a los datos datos de transporte del Documento electrónico. <br/>Ver detalle en tabla [data.transporte](#parametro-del-objeto-data-transporte).<br/>
documentoAsociado|No|Conjunto de información relacionada a los datos documentos asociados del Documento electrónico. <br/>Ver detalle en tabla [data.documentoAsociado](#parametro-del-objeto-data-documentoasociado).<br/>
descuentoGlobal|No|Descuento global de la Operación<br/>**Campo XML:** Relacionado a EA004
anticipoGlobal|No|Anticipo global de la Operación<br/>**Campo XML:** Relacionado a EA007
extras|No|Objeto de datos extras del Documento Electronico en formato **key=value** que puede ser enviado de forma adicional para cualquier necesidad del emisor. <br/><br/>El mismo puede ser utilizado para mostrar en el **KUDE** o para fines de integracion ya que envia en el **Webhook**.<br/><br/>Ej.:<br/>"extras" : {<br/>&nbsp;&nbsp;"pedidoCliente" : "2123-1", <br/>&nbsp;&nbsp;"numeroPresupuesto": "P/001", <br/>&nbsp;&nbsp;"posTicketId" : 39271<br/>}<br/>
format|No|Indica la configuración del formato de impresión (Factura, Ticket o Personalizado) con el cual se guardará el Documento Electrónico, y el cual será su valor por defecto. Si no se pasa éste atributo, se asumirá el configurado en el establecimiento a travez de la consola.<br/><br/>Al enviar un DE por correo o imprimir un ticket se utilizará ésta opción guardada. <br/><br/>También podrá, posteriormente, indicar explicitamente el formato que desea al momento de obtener el PDF del KUDE<br/><br/>Posibles Valores:<br/>**ticket**=Especifica que el KUDE del DE quedará guardado en modo Ticket<br/>**custom**=Especifica que el KUDE del DE quedará guardado con el formato personalizado. (Sólo vàlido para tipoDocumento=1) <br/><br/>Para emitir en formato normal ignore ésta opción<br/>

### Parametro del objeto data.cliente

Parámetro | Requerido | Descripción
--------- | --------- | -----------
**contribuyente** |**Si**|Si el receptor(Cliente) del DE es contribuyente  Valores: true o false  <br/>**Campo XML:** D201
ruc |No| R.U.C. del Cliente, Obligarorio si es contribuyente. <br/>**Campo XML:** D206
**razonSocial**|**Si**| Nombre o Razon social del cliente,En caso de DE innominado,completar con “Sin Nombre” <br/>**Campo XML:** D211
nombreFantasia |No|Nombre de fantasia del cliente <br/>**Campo XML:** D212
**tipoOperacion**|**Si**|Tipo de operación(1= B2B, 2= B2C, 3= B2G, 4= B2F)<br/>**Campo XML:** D202
direccion |No|Direccion del Cliente, Campo obligatorio cuando tipoDocumento =7 o tipoOperacion=4 <br/>**Campo XML:** D213
numeroCasa|No|Numero de Casa del Cliente, Campo obligatorio si se informa la direccion,Cuando es contribuyente debe corresponder a lo declarado en el RUC<br/>**Campo XML:** D218
departamento|No| Código del departamento,Campo obligatorio si se informa la dirección y tipoOperacion ≠ 4, no se debe informar cuando tipoOperacion = 4.<br/>**Campo XML:** D219 
distrito|No|Código del distrito del Cliente, El  código debe seguir la Tabla 2.1 – Distritos del Manual Tecnico. <br/>**Campo XML:** D221
ciudad|No|Código de la ciudad del Cliente. Campo obligatorio si se informa la dirección y tipoOperacion≠4, no se debe informar cuando tipoOperacion = 4.<br/>**Campo XML:**D223
**pais**|**Si**|Código del Pais del Cliente, Segun XSD de Codificación de Países<br/>**Campo XML:**D203
tipoContribuyente|No|Tipo de contribuyente Ej.: 1= Persona Física, 2= Persona Jurídica<br/>Obligatorio si contribuyente = true, No informar si contribuyente = false<br/>**Campo XML:**D205
documentoTipo|No|Tipo de documento del cliente, de acuerdo a <br/><br/>1=Cédula paraguaya<br/>2=Pasaporte<br/>3=Cédula extranjera<br/>4=Carnet de residencia<br/>5=Innominado<br/>6=Tarjeta Diplomática de exoneración fiscal<br/>9=Informar data.documentoTipoDescripcion<br/><br/>**Campo XML:**D208
documentoNumero|No|Número de documento de identidad.Obligatorio si contribuyente = false y tipoOperacion ≠ 4.<br/>En caso de DE innominado, completar con 0 (cero)<br/>**Campo XML:**D210
telefono|No|Número de teléfono. Debe incluir el prefijo de la ciudad si pais = PRY<br/>**Campo XML:**D214
celular|No|Numero de celular del cliente <br/>**Campo XML:**D215
email|No|Correo electronico del cliente<br/><br/>Si se le pasa más de un correo (separado por comas) en eKuatia se incluirá sólo el primero<br/><br/>**Campo XML:**D216
codigo|No|Código del Cliente<br/>**Campo XML:**D217

### Parametro del objeto data.usuario
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**documentoTipo**|**Si**|Tipo de documento de identidad del responsable de la generación del DE<br/>**Campo XML:**D141
**documentoNumero**|**Si**|Número de documento de identidad del responsable de la generación del DE<br/>**Campo XML:**D143
**nombre**|**Si**|Nombre o razón social del responsable de la generación del DE<br/>**Campo XML:**D144
**cargo**|**Si**|Cargo del responsable de la generación del DE<br/>**Campo XML:**D145
**email**|No|Email del responsable de la generación del DE (Esta información no se envía a la SET)<br/><br/>Si se pasa un email válido, también se notifican a éste correo los mensajes de FacturaSend.<br/>

### Parametro del objeto data.factura

Parámetro | Requerido | Descripción
--------- | --------- | -----------
presencia|Si|Indicador de presencia<br/>1= Operación presencial<br/>2= Operación electrónica<br/>3= Operación telemarketing<br/>4= Venta a domicilio<br/>5= Operación bancaria<br/>6= Operación cíclica<br/>9= Otro<br/>**Campo XML:** E011
fechaEnvio|No|Fecha futura del traslado de mercadería<br/>**Campo XML:** E013
dncp|No|Campos de informaciones de Compras Públicas.Ver detalle en tabla [data.factura.dncp]

### Parametro del objeto data.factura.dncp

Parámetro | Requerido | Descripción
--------- | --------- | -----------
**modalidad**|**Si**|Modalidad - Código emitido por la DNCP <br/>**Campo XML:** E021
**entidad**|**Si**|Entidad - Código emitido por la DNCP<br/>**Campo XML:** E022
**año**|**Si**|Año - Código emitido por la DNCP<br/>**Campo XML:** E023
**secuencia**|**Si**|Secuencia - emitido por la DNCP <br/>**Campo XML:** E024
**fecha**|**Si**|Fecha de emisión del código de contratación por la DNCP<br/>**Campo XML:** E025

### Parametro del objeto data.autoFactura

Parámetro | Requerido | Descripción
--------- | --------- | -----------
**tipoVendedor**|**Si**|Naturaleza del vendedor <br/>1= No contribuyente <br/>2= Extranjero <br/>**Campo XML:** E301
**documentoTipo**|**Si**|Tipo de documento de identidad del vendedor <br/>**Campo XML:** E304
**documentoNumero**|**Si**| Número de documento de identidad del vendedor<br/>**Campo XML:** E306
**nombre**|**Si**|Nombre y apellido del vendedor  <br/>**Campo XML:** E307
**direccion**|**Si**|Dirección del vendedor.En caso de extranjeros, colocar la dirección en donde se realizó la transacción. <br/>**Campo XML:** E308
**numeroCasa**|**Si**|Número de casa del vendedor.Si no tiene numeración colocar 0 (cero)  <br/>**Campo XML:** E309
**departamento**|**Si**|Código del departamento del vendedor  <br/>**Campo XML:** E310
departamentoDescripcion|No|Descripción del departamento del vendedor <br/>**Campo XML:** E311
**distrito**|**Si**|Código del distrito del vendedor <br/>**Campo XML:** E312
distritoDescripcion|No|Descripción del distrito del vendedor <br/>**Campo XML:** E313
**ciudad**|**Si**|Código de la ciudad del vendedor <br/>**Campo XML:** E314
ciudadDescripcion|No|Descripción del ciudad del vendedor <br/>**Campo XML:** E315
**ubicacion**|**Si**| Ver detalle en tabla [data.autoFactura.ubicacion](#parametro-del-objeto-data-autofactura-ubicacion)

### Parametro del objeto data.autoFactura.ubicacion

Parámetro | Requerido | Descripción
--------- | --------- | -----------
**lugar**|**Si**| Lugar de la transacción <br/>**Campo XML:** E316
**departamento**|**Si**|Código del departamento donde se realiza la transacción <br/>**Campo XML:** E317
departamentoDescripcion|No| Descripcion del departamento donde se realiza la transacción <br/>**Campo XML:** E318
**distrito**|**Si**|<br/>Código del distrito donde se realiza la transacción **Campo XML:** E319
distritoDescripcion|No| Descripcion del distrito donde se realiza la transacción <br/>**Campo XML:** E320
**ciudad**|**Si**| Código de la ciudad donde se realiza la transacción <br/>**Campo XML:** E321 
ciudadDescripcion|No|Descripcion de la ciudad donde se realiza la transacción  <br/>**Campo XML:** E322 

### Parametro del objeto data.notaCreditoDebito

Parámetro | Requerido | Descripción
--------- | --------- | -----------
motivo|Si|Motivo de la emisión<br/>1= Devolución y Ajuste de precios<br/>2= Devolución<br/>3= Descuento<br/>4= Bonificación<br/>5= Crédito incobrable<br/>6= Recupero de costo<br/>7= Recupero de gasto<br/>8= Ajuste de precio<br/><br/>**Campo XML:** E401

### Parametro del objeto data.remision

Parámetro | Requerido | Descripción
--------- | --------- | -----------
motivo|Si|Valor numério del Motivo de la emisión:<br/>1= Traslado por venta<br>2= Traslado por consignación<br>3= Exportación<br>4= Traslado por compra<br>5= Importación<br>6= Traslado por devolución<br>7= Traslado entre locales de la empresa<br>8= Traslado de bienes por transformación<br>9= Traslado de bienes por reparación<br>10= Traslado por emisor móvil<br>11= Exhibición o demostración<br>12= Participación en ferias<br>13= Traslado de encomienda<br>14= Decomiso<br>99=Otro (deberá consignarse expresamente el o los motivos diferentes a los mencionados anteriormente)<br><br>Obs.: Cuando el motivo sea por operaciones internas de la empresa, el RUC del receptor debe ser igual al RUC del emisor.<br><br>**Campo XML:** E501
motivoDescripcion|No|Descripción del Motivo de la emisión, caso el motivo sea igual a 99<br><br>**Campo XML:** E502
tipoResponsable|Si|Responsable de la emisión de la Nota Remisión Electrónica:<br>1= Emisor de la factura<br>2= Poseedor de la factura y bienes<br>3= Empresa transportista<br>4= Despachante de Aduanas<br>5= Agente de transporte o intermediario<br><br>**Campo XML:** E503, E504
kms|Si|Kilómetros estimados de recorrido<br><br>**Campo XML:** E505
fechaFactura|No|Fecha futura de emisión de la factura (AAAA-MM-DD)<br><br>**Campo XML:** E506
costoFlete|No|Costo del Flete N(15,8)<br><br>**Campo XML:** E507

### Parametro del objeto data.items
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**codigo** |**Si**|Código interno de identificación de la mercadería o servicio de responsabilidad del emisor<br/>**Campo XML:** E701 
**descripcion**|**Si** |Descripción del producto y/o servicio. Equivalente a nombre del producto establecido en la RG 24/2019<br/>**Campo XML:** E708
observacion|No|Informacion de intetes acerca del item<br/>**Campo XML:** E714
partidaArancelaria|No|Partida arancelaria<br/>**Campo XML:** E702
ncm|No|Nomenclatura común del Mercosur (NCM)<br/>**Campo XML:** E703
**unidadMedida**|**Si**|Es la unidad de medida del producto <br/>**Campo XML:** E709
**cantidad**|**Si**|Cantidad del producto y/o servicio <br/>**Campo XML:** E711
**precioUnitario**|**Si**|Precio unitario del producto y/o servicio (incluidos impuestos)<br/>**Campo XML:** E721
cambio|No|Tipo de cambio por ítem<br/>**Campo XML:** E725
descuento|No|Descuento particular sobre el precio unitario por ítem (incluidos impuestos)<br/>**Campo XML:** EA002
anticipo|No|Anticipo particular sobre el precio unitario por ítem (incluidos impuestos)<br/>**Campo XML:** EA006
pais|No|<br/>Código del país de origen del producto**Campo XML:** E712
paisDescripcion|No|Nombre del país de origen del producto<br/>**Campo XML:** E713
tolerancia|No|Código de tolerancia de merma de los productos<br/>Opcional si C002 = 7<br/><br/> 1=Tolerancia de quiebra<br/>2= Tolerancia de merma<br/><br/>Según RG 41/14. **Campo XML:** E715
toleranciaCantidad|No|Cantidad de quiebra o merma<br/><br/>Obligatorio si se envia la tolerancia<br/>**Campo XML:** E717
toleranciaPorcentaje|No|Porcentaje de quiebra o merma<br/><br/>Obligatorio si se envia la tolerancia<br/>**Campo XML:** E718
cdcAnticipo|No|CDC del anticipo<br/>**Campo XML:** E719
**ivaTipo** |**Si**|Forma de afectación tributaria del IVA <br/>1= Gravado IVA<br/>2= Exonerado (Art. 83- Ley 125/91) <br/>3= Exento <br/>4= Gravado parcial Grav-Exento)<br/>**Campo XML:** E731
**ivaBase**|**Si**|Base gravada del IVA por ítem<br/>**Campo XML:** E735
**iva**|**Si**|Tasa del IVA<br/>Posibles valores = 0, 5 o 10<br/><br/>**Campo XML:** E734
lote|No|Numero de Lote del producto<br/>Valor alfanumérico<br/>Longitud: [1-80]<br/><br/>**Campo XML:** E751
vencimiento|No|Fecha de vencimiento del producto Formato AAAA-MM-DD<br/>**Campo XML:** E752
numeroSerie|No|Número de serie <br/>Valor alfanumérico<br/>Longitud: [1-10]<br/><br/>**Campo XML:** E753
numeroPedido|No|Número de pedido<br/>**Campo XML:** E754
numeroSeguimiento|No|Número de seguimiento del envío<br/>**Campo XML:** E755
registroSenave|No|Número de registro del producto otorgado por el SENAVE<br/>Obligados por la RG N° 16/2019 y la RG N° 24/2019 – Agroquímicos<br/>**Campo XML:** E759
registroEntidadComercial|No|Número de registro de entidad comercial otorgado por el SENAVE<br/><br/>**Campo XML: **E760
nombreProducto|No|Obligados por el Art. 1 de la RG N° 106/2021 – Agroquímicos<br/><br/>**Campo XML: **E761
dncp|No|Identificación de los datos de la DNCP<br/>Ver detalle en tabla [data.items.dncp](#parametro-del-objeto-data-items-dncp)<br/>
extras|No|Objeto de datos extras del item en formato **key=value** que puede ser enviado de forma adicional por cada item para cualquier necesidad del emisor. <br/><br/>El mismo puede ser utilizado para mostrar en el **KUDE** o para fines de integracion ya que envia en el **Webhook**.<br/><br/>Ej.:<br/>"extras" : {<br/>&nbsp;&nbsp;"taxRate" : "15%", <br/>&nbsp;&nbsp;"barCode": "7937638273256", <br/>&nbsp;&nbsp;"storeId" : 3<br/>}<br/>

### Parametro del objeto data.items.dncp

Parámetro | Requerido | Descripción
--------- | --------- | -----------
codigoNivelGeneral|No|Código DNCP – Nivel General. Obligatorio si tipoOperacion = 3 <br/>**Campo XML:** E704
codigoNivelEspecifico|No|Código DNCP – Nivel Especifico. Obligatorio si existe el campo codigoNivelGeneral <br/>**Campo XML:** E705
codigoGtinProducto|No|Código GTIN por producto. Informar si la mercadería tiene GTIN <br/>**Campo XML:** E706
codigoNivelPaquete|No|Código GTIN por paquete. Informar si el paquete tiene GTIN<br/>**Campo XML:** E707

<!---
se retira en nt 009
### Parametro del objeto data.items.importador

Parámetro | Requerido | Descripción
--------- | --------- | -----------
nombre|No|Nombre del Importador. Obligados por la RG N° 16/2019 – Agroquímicos<br/>**Campo XML:** E756
direccion|No|Dirección de Importador<br/>**Campo XML:** E757
registroImportador|No|Número de registro de la firma del importador<br/>**Campo XML:** E758
-->

### Parametro del objeto data.items.sectorAutomotor

Parámetro | Requerido | Descripción
--------- | --------- | -----------
tipo|No|Tipo de operación de venta de vehículos<br/>1= Venta a representante<br/>2= Venta al consumidor final<br/>3= Venta a gobierno<br/>4= Venta a flota de vehículos<br/>**Campo XML:** E771
chasis|No|Chasis del vehículo<br/>**Campo XML:** E773
color|No|Color del vehículo<br/>**Campo XML:** E774
potencia|No|Potencia del motor (CV) <br/>**Campo XML:** E775
capacidadMotor|No|Capacidad del motor. Expresa en centímetros cúbicos (cc) <br/>**Campo XML:** E776
capacidadPasajeros|No|Capacidad máxima de pasajeros sentados<br/>**Campo XML:** E785
pesoBruto|No|Peso bruto del vehiculo. En toneladas<br/>**Campo XML:** E778
pesoNeto|No|Peso neto del vehiculo. En toneladas<br/>**Campo XML:** E777
tipoCombustible|No|Tipo de combustible <br/>1= Gasolina<br/>2= Diésel<br/>3= Etanol<br/>4= GNV<br/>5= Flex<br/>9= Otro<br/>**Campo XML:** E779
tipoCombustibleDescripcion|No|Descripción del tipo de combustible. <br/>**Campo XML:** E780
numeroMotor|No|<br/>Número del motor**Campo XML:** E781
capacidadTraccion|No|Capacidad máxima de tracción <br/>**Campo XML:** E782
año|No|Año de fabricación<br/>**Campo XML:** E783
tipoVehiculo|No|Tipo de vehículo<br/>**Campo XML:** E784
cilindradas|No|Cilindradas del motor<br/>**Campo XML:** E786

### Parametro del objeto data.condicion

Parámetro | Requerido | Descripción
--------- | --------- | -----------
**tipo**|**Si**|Condición de la operación. <br/>1= Contado <br/>2= Crédito<br/>**Campo XML:** E601
entregas|No|Datos que describen la forma de pago al contado o del monto de la entrega inicial. Ver detalle en tabla [data.condicion.entregas](#parametros-del-objeto-data-condicion-entregas).<br/>
credito|No|Campos que describen la operación a crédito. Ver detalle en tabla [data.condicion.credito](#parametros-del-objeto-data-condicion-credito).<br/>

### Parametros del objeto data.condicion.entregas
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**tipo**|**Si**|Tipo de pago Ej.:1= Efectivo, 2= Cheque,3= Tarjeta de crédito, 4= Tarjeta de débito. Existe mas tipos de pagos ver en: <br/> **Campo XML:** E606
tipoDescripcion|No|Descripción del Tipo de pago. Cuando el tipo = 99 es obligatorio especificar el tipo de pago personalizado : <br/> **Campo XML:** E607
**monto**|**Si**| Monto por tipo de pago <br/> **Campo XML:** E608
**moneda**|**Si**|Moneda por tipo de pago<br/>Según tabla de códigos para monedas de acuerdo con la norma ISO 4217 Se requiere la misma moneda para todos los ítems del DE<br/> **Campo XML:** E609
cambio|No|Tipo de cambio por tipo de pago.<br/>Obligatorio si moneda ≠ PYG <br/> **Campo XML:** E611
infoTarjeta|No|Campos que describen el pago o entrega inicial de la operación con tarjeta de crédito/débito. Ver detalle en tabla [data.condicion.entregas.infoTarjeta](#parametros-del-objeto-data-condicion-entregas-infotarjeta)
infoCheque|No|Campos que describen el pago o entrega inicial de la operación con cheque. Ver detalle en [tabla data.condicion.entregas.infoCheque](#parametros-del-objeto-data-condicion-entregas-infocheque)
extras|No|Objeto de datos extras de la entrega en formato **key=value** que puede ser enviado de forma adicional por cada condicion de entrega para cualquier necesidad del emisor. <br/><br/>El mismo puede ser utilizado para mostrar en el **KUDE** o para fines de integracion ya que envia en el **Webhook**.<br/><br/>Ej.:<br/>"extras" : {<br/>&nbsp;&nbsp;"vuelto" : 8500, <br/>&nbsp;&nbsp;"numeroDoc": "T-3232323"<br/>}<br/>


### Parametros del objeto data.condicion.entregas.infoTarjeta
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**tipo**|**Si**|Denominación de la tarjeta.<br/>1= Visa<br/>2= Mastercard<br/>3= American Express<br/>4= Maestro<br/>5= Panal<br/>6= Cabal<br/>99= Otro <br/>**Campo XML:** E621
**tipoDescripcion**|**Si**|<br/>Descripción de denominación de la tarjeta. Si tipo =99 informar la descripción de la denominación de la tarjeta**Campo XML:** E622
numero|No|Número de la tarjeta. Cuatro últimos dígitos de la tarjeta<br/>**Campo XML:** E629
titular|No|Nombre del titular de la tarjeta <br/>**Campo XML:** E628
ruc|No|RUC de la procesadora de tarjeta<br/>**Campo XML:** E624
razonSocial|No|Razón social de la procesadora de tarjeta<br/>**Campo XML:** E623
**medioPago**|**Si**|Forma de procesamiento de pago.<br/>1= POS. <br/>2= Pago Electrónico (Ejemplo:compras por Internet)<br/>9= Otro<br/>**Campo XML:** E626
codigoAutorizacion|No|Código de autorización de la operación <br/>**Campo XML:** E627
    
### Parametros del objeto data.condicion.entregas.infoCheque
Parámetro | Requerido | Descripción
--------- | --------- | -----------     
**numeroCheque**|**Si**|Número de cheque. Completar con 0 (cero) a la izquierda hasta alcanzar 8 (ocho) cifras<br/>**Campo XML:** E631
**banco**|**Si**|Banco emisor<br/>**Campo XML:** E632

### Parametros del objeto data.condicion.credito
Parámetro | Requerido | Descripción
--------- | --------- | -----------   
**tipo**|**Si**|Condición de la operación a crédito <br/>1= Plazo <br/>2= Cuota<br/>**Campo XML:** E641
plazo |No|Plazo del crédito. Obligatorio si tipo = 1 <br/>Ejemplo: 30 días, 12 meses<br/>**Campo XML:** E643
cuotas|No|Cantidad de cuotas. Plazo del crédito.  Obligatorio si tipo = 2<br/>Ejemplo: 12, 24, 36 <br/>**Campo XML:** E644
infoCuotas|No|Campos que describen las cuotas.Ver detalle en tabla [data.condicion.credito.infoCuotas](#parametros-del-objeto-data-condicion-credito-infocuotas)

### Parametros del objeto data.condicion.credito.infoCuotas
Parámetro | Requerido | Descripción
--------- | --------- | ----------- 
**moneda**|**Si**|Moneda de las cuotas.Según tabla de códigos para monedas de acuerdo con la norma ISO 4217 <br/>**Campo XML:** E653
**monto**|**Si**|Monto de cada cuota<br/>**Campo XML:** E651
vencimiento|No|Fecha de vencimiento de cada cuota<br/>**Campo XML:** E652

### Parametro del objeto data.sectorEnergiaElectrica
Parámetro | Requerido | Descripción
--------- | --------- | ----------- 
numeroMedidor|No|Número de medidor<br/>**Campo XML:** E792
codigoActividad|No|Código de actividad<br/>**Campo XML:** E793
codigoCategoria|No|Código de categoría E<br/>**Campo XML:** E794
lecturaAnterior|No|Lectura anterior<br/>**Campo XML:** E795
lecturaActual|No|Lectura actual <br/>**Campo XML:** E796
### Parametro del objeto data.sectorSeguros
Parámetro | Requerido | Descripción
--------- | --------- | ----------- 
codigoAseguradora|No|Código de la empresa de seguros en la Superintendencia de Seguros<br/>**Campo XML:** E801
**codigoPoliza**|**Si**|Código de la póliza<br/>**Campo XML:** EA791
**numeroPoliza**|**Si**|Número de la póliza<br/>**Campo XML:** EA794
**vigencia**|**Si**|Descripción de la unidad de tiempo de vigencia<br/>**Campo XML:** EA792
**vigenciaUnidad**|**Si**|Vigencia de la póliza<br/>**Campo XML:** EA793
inicioVigencia|No|Fecha de inicio de vigencia<br/>**Campo XML:** EA795
finVigencia|No|Fecha de fin de vigencia <br/>**Campo XML:** EA796
codigoInternoItem|No|Código interno del ítem<br/>**Campo XML:** EA797

### Parametro del objeto data.sectorSupermercados
Parámetro | Requerido | Descripción
--------- | --------- | ----------- 
nombreCajero|No|Nombre del cajero<br/>**Campo XML:** E811
efectivo|No|Efectivo<br/>**Campo XML:** E812
vuelto|No|Vuelto<br/>**Campo XML:** E813
donacion|No|Monto de la donación<br/>**Campo XML:** E814
donacionDescripcion|No|Descripción de la donación<br/>**Campo XML:** E815

### Parametro del objeto data.sectorAdicional
Parámetro | Requerido | Descripción
--------- | --------- | ----------- 
ciclo|No|Ciclo<br/>**Campo XML:** E821
inicioCiclo|No|Fecha de inicio de ciclo<br/>**Campo XML:** E822
finCiclo|No|Fecha de fin de ciclo<br/>**Campo XML:** E823
vencimientoPago|No|Fecha de vencimiento para el pago<br/>**Campo XML:** E824
numeroContrato|No|Número de contrato E<br/>**Campo XML:** E825
saldoAnterior|No|Saldo anterior<br/>**Campo XML:** E826

### Parametro del objeto data.transporte
Parámetro | Requerido | Descripción
--------- | --------- | ----------- 
tipo|No|Tipo de transporte. Obligatorio si tipoDocumento = 7. <br/>1= Propio<br/>2= Tercero<br/>**Campo XML:** E901
**modalidad**|**Si**|Modalidad del transporte<br/>1=Terrestre<br/>2= Fluvial<br/>3= Aéreo<br/>4= Multimodal<br/>**Campo XML:** E903
**tipoResponsable**|**Si**|Responsable del costo del flete<br/>1= Emisor de la Factura Electrónica<br/>2= Receptor de la Factura Electrónica <br/>3= Tercero<br/>4= Agente intermediario del transporte (cuando intervenga)<br/>5= Transporte propio <br/>**Campo XML:** E905
condicionNegociacion|No|Condición de la negociación segun las opciones:<br/><br/>CFR Costo y flete<br/>CIF Costo, seguro y flete<br/>CIP Transporte y seguro pagados hasta<br/>CPT Transporte pagado hasta<br/>DAP Entregada en lugar convenido<br/>DAT Entregada en terminal<br/>DDP Entregada derechos pagados<br/>EXW En fabrica<br/>FAS Franco al costado del buque<br/>FCA Franco transportista<br/>FOB Franco a bordo<br/><br/>**Campo XML: **E906
numeroManifiesto|No|Número de manifiesto o conocimiento de carga/declaración de tránsito aduanero/ Carta de porte internacional <br/>**Campo XML:** E907
numeroDespachoImportacion|No|Número de despacho de importación<br/>**Campo XML:** E908
inicioEstimadoTranslado|No|Fecha estimada de inicio de traslado<br/>**Campo XML:** E909
finEstimadoTranslado|No|Fecha estimada de fin de traslado<br/>**Campo XML:** E910
paisDestino|No|Código del país de destino <br/>**Campo XML:** E911
paisDestinoNombre|No|Descripción del país de destino.  <br/>**Campo XML:** E912
salida|No|Campos que identifican el local de salida de las mercaderías. <br/>Obligatorio si tipoDocumento = 7.<br/> Ver detalle en tabla [data.transporte.salida](#parametro-del-objeto-data-transporte-salida)
entrega|No|Campos que identifican el local de entrega de las mercaderías. <br/>Obligatorio si tipoDocumento = 7.<br/> Ver detalle en tabla [data.transporte.entrega](#parametro-del-objeto-data-transporte-entrega)
vehiculo|No|Campos que identifican el vehículo de traslado de mercaderías. <br/>Obligatorio si tipoDocumento = 7.<br/> Ver detalle en tabla [data.transporte.vehiculo](#parametro-del-objeto-data-transporte-vehiculo)
transportista|No|Campos que identifican al transportista. <br/>Obligatorio si tipoDocumento = 7.<br/> Ver detalle en tabla [data.transporte.transportista](#parametro-del-objeto-data-transporte-transportista)

### Parametro del objeto data.transporte.salida
Parámetro | Requerido | Descripción
--------- | --------- | ----------- 
**direccion**|**Si**|Dirección del local de salida. Nombre de la calle principal <br/>**Campo XML:** E921
**numeroCasa**|**Si**|Número de casa de salida<br/>**Campo XML:** E922
complementoDireccion1|No|Complemento de dirección 1 salida. Nombre de la calle secundaria<br/>**Campo XML:** E923
complementoDireccion2|No|Complemento de dirección 2 salida. Número de departamento/piso/ local/ edificio/ deposito del local de salida de la mercadería<br/>**Campo XML:** E924
**departamento**|**Si**|Código del departamento del local de salida. Según XSD de Departamentos<br/>**Campo XML:** E925
**departamentoDescripcion**|**Si**|Descripción del departamento del local de salida<br/>**Campo XML:** E926
distrito|No|Código del distrito del local de salida<br/>**Campo XML:** E927
distritoDescripcion|No|Descripción de distrito del local de salida<br/>**Campo XML:** E927
**ciudad**|**Si**|Código de la ciudad del local de salida<br/>**Campo XML:** E929
**ciudadDescripcion**|**Si**|Descripción de ciudad del local de salida<br/>**Campo XML:** E930
pais|No|Código del país del local de salida
paisDescripcion|No|Descripción del país del local de salida
telefonoContacto|No|Teléfono de contacto del local de salida<br/>**Campo XML:** E931 


### Parametro del objeto data.transporte.entrega
Parámetro | Requerido | Descripción
--------- | --------- | ----------- 
**direccion**|**Si**|Dirección del local de entrega. Nombre de la calle principal <br/>**Campo XML:** E941
**numeroCasa**|**Si**|Número de casa de entrega<br/>**Campo XML:** E942
complementoDireccion1|No|Complemento de dirección 1 entrega. Nombre de la calle secundaria<br/>**Campo XML:** E943
complementoDireccion2|No|Complemento de dirección 2 salida. Número de departamento/piso/ local/ edificio/ deposito del local de salida de la mercadería<br/>**Campo XML:** E944
**departamento**|**Si**|Código del departamento del local de entrega. Según XSD de Departamentos<br/>**Campo XML:** E945
**departamentoDescripcion**|**Si**|Descripción del departamento del local de salida<br/>**Campo XML:** E946
distrito|No|Código del distrito del local de entrega<br/>**Campo XML:** E947
distritoDescripcion|No|Descripción de distrito del local de entrega<br/>**Campo XML:** E948
**ciudad**|**Si**|Código de la ciudad del local de salida<br/>**Campo XML:** E949
**ciudadDescripcion**|**Si**|Descripción de ciudad del local de salida<br/>**Campo XML:** E950
pais|No|Código de  pais de salida
paisDescripcion|No|Descripcion del pais de salida
telefonoContacto|No|Teléfono de contacto del local de la entrega<br/>**Campo XML:** E951 

### Parametro del objeto data.transporte.vehiculo
Parámetro | Requerido | Descripción
--------- | --------- | ----------- 
**tipo**|**Si**|Tipo de vehículo. Ejemplo: Camioneta, Barcaza, Elicoptero.<br/><br/>Debe ser acorde al atributo **modalidad**(E903)<br/><br/>**Campo XML:** E961
**marca**|**Si**|Marca<br/>**Campo XML:** E962
**documentoTipo**|**Si**|Tipo de identificación del vehículo <br/>1=Número de identificación del vehículo<br/>2=Número de matrícula del vehículo<br/>**Campo XML:** E967
documentoNumero|No|Número de identificación del vehículo. Debe informarse cuando el documentoTipo=1<br/>**Campo XML:** E963
obs|No|Datos adicionales del vehículo <br/>**Campo XML:** E964
numeroMatricula|No|Número de matrícula del vehículo. Debe informarse cuando el documentoTipo=2 <br/>**Campo XML:** E965
numeroVuelo|No|Número de vuelo<br/>**Campo XML:** E966

### Parametro del objeto data.transporte.transportista
Parámetro | Requerido | Descripción
--------- | --------- | ----------- 
**contribuyente**|**Si**|Naturaleza del transportista(true o false)<br/>**Campo XML:** E980
**nombre**|**Si**|Nombre o razón social del transportista <br/>**Campo XML:** E982
**ruc**|**Si**|RUC del transportista<br/>**Campo XML:** E983
documentoTipo|No|Tipo de documento de identidad del transportista<br/>Obligatorio si contribuyente=false<br/><br/>Valores:<br/>1=Cédula paraguaya<br/>2=Pasaporte<br/>3=Cédula extranjera<br/>4=Carnet de residencia<br/><br/>**Campo XML:** E985
documentoNumero|No|Número de documento de identidad del transportista. Obligatorio si existe el campo documentoTipo<br/>**Campo XML:** E987
**direccion**|Si|Domicilio fiscal del transportista<br/>**Campo XML:** E992
obs|No|Observacion del transportista
pais|No|Código del pais de Origen del transportista
paisDescripcion|No|Descripcion del pais Origen
chofer|Si|Campos que identifican al chofer. Ver detalle en tabla [data.transporte.transportista.chofer](#parametro-del-objeto-data-transporte-transportista-chofer)
agente|No|Campos que identifican al agente. Ver detalle en tabla [data.transporte.transportista.agente](#parametro-del-objeto-data-transporte-transportista-agente)

### Parametro del objeto data.transporte.transportista.chofer
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**documentoNumero**|**Si**|Número de documento de identidad del chofer<br/>**Campo XML:** E990
**nombre**|**Si**|Nombre y apellido del chofer <br/>**Campo XML:** E991
direccion|Si|Dirección del chofer<br/>**Campo XML:** E993

### Parametro del objeto data.transporte.transportista.agente
Parámetro | Requerido | Descripción
--------- | --------- | -----------
nombre|No|Nombre o razón social del agente. Casos particulares según RG N°41/14 <br/>**Campo XML:** E994
ruc|No|RUC del agente<br/>**Campo XML:** E995
direccion|No|Dirección del agente<br/>**Campo XML:** E997

### Parametro del objeto data.complementarios
Parámetro | Requerido | Descripción
--------- | --------- | -----------
ordenCompra|No|Número de orden de compra<br/>**Campo XML:** G002
ordenVenta|No|Número de orden de venta<br/>**Campo XML:** G003
numeroAsiento|No|Número de asiento contable <br/>**Campo XML:** G004
carga|No|Campos generales de la carga

### Parametro del objeto data.complementarios.carga
Parámetro | Requerido | Descripción
--------- | --------- | -----------
unidadMedidaVolumenTotal|No|Unidad de medida del total de volumen de la mercadería <br/>**Campo XML:** G051
volumenTotal|No|Volumen total de la mercadería <br/>**Campo XML:** G053
unidadMedidaPesoTotal|No|Unidad de medida del peso total de la mercadería<br/>**Campo XML:** G054
pesoTotal|No|Peso total de la mercadería<br/>**Campo XML:** G056
caracteristicaCarga|No|1 – Mercaderías con cadena de frío<br/>2 – Carga peligrosa <br/>3 – Otro de características similares (especificar)<br/>Obligatorio cuando lo exige la RG 41/14<br/>**Campo XML:** G057
caracteristicaCargaDescripcion|No|Descripcion de la caracteristica de carga<br/>Solo especificar cuando caracteristicaCarga = 3<br/>**Campo XML:** G058

### Parametro del objeto data.documentoAsociado
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**formato**|**Si**|Tipo de documento asociado<br/>1= Electrónico<br/>2= Impreso<br/>3= Constancia Electrónica <br/>**Campo XML:** H002
cdc|No|CDC del DTE referenciado <br/>**Campo XML:** H004
tipoDocumentoImpreso|**Si**|Tipo de documento impreso:<br/>1= Factura<br/>2= Nota de crédito<br/>3= Nota de débito<br/>4= Nota de remisión<br/>5= Comprobante de retención<br/><br/>**Campo XML:** H009
timbrado|**Si**|Nro. timbrado documento impreso de referencia<br/>**Campo XML:** H005
establecimiento|**Si**|Establecimiento<br/>**Campo XML:** H005
punto|**Si**|Punto de expedición<br/>**Campo XML:** H007
numero|**Si**|Número del documento<br/>**Campo XML:** H008
fecha|**Si**|Fecha de emisión del documento impreso de referencia. Obligatorio si existe el campo establecimiento.<br/>Formato AAAA-MM-DD <br/>No Informar si campo establecimiento no existe<br/>**Campo XML:** H011
numeroRetencion|No|Número de comprobante de retención <br/>**Campo XML:** H012
resolucionCreditoFiscal|No|Número de resolución de crédito fiscal <br/>**Campo XML:** H013
constanciaTipo|No|Tipo de constancia<br/>**Campo XML:** H014
constanciaNumero|No|Numero de constancia<br/>**Campo XML:** H016
constanciaControl|No|Código de Control de la constancia<br/>**Campo XML:** H017

## Respuesta de creación de un DE
> Ejemplo de respuesta de creación de un DE:

```json
{ 
  "success" : true,
  "deList" : [{
    "cdc": "01800695631001002100694612021112410311184194",
    "numero": "001-001-0000001",
    "estado": "Aprobado",
    "respuesta_codigo": "",
    "respuesta_mensaje": ""
  }],
  "loteId" : 12
}
```

La respuesta de creación de un documento electrónico, representa la estructura de datos JSON que retorna la API de FacturaSend luego de haber solicitado la creación de un DE.

Abajo se describe el detalles de los atributos.

### Respuesta
La respuesta de éste Servicio:

Atributos | Tipo | Description
--------- | ---- | -----------
success | boolean | true si no hubo errores en la transacción
error | string | El mensaje de Error, en el caso de que el success = false, Si la invocación se realizó para crear 1 sólo DE por el método sincrono, entonces aquí se especificará el mensaje de error.
errores | array | En el caso de haya invocado la API para crear varios DEs por el método asíncrono, aqui se mostrarán una lista de errores, indicando el error, y el número de índice del archivo XML con Error.
deList | array | El array con la respuesta de cada DE procesado. Este array siempre devolverá 1 (un) sólo elemento para el elemento síncrono, pero es del tipo array por compatibilidad con el envío por asincrono o por lotes<br><br>Los atributos de éste array se describen en Respuesta [deList](#atributos-de-la-respuesta-delist)
loteId | number | El número de lote generado para la solicitud.

### Atributos de la Respuesta deList

Atributos | Tipo | Description
--------- | ---- | -----------
cdc | string | Id único de 44 dígitos generado para el Documento Electrónico
numero | string | Número de Documento Electrónico generado en formato 001-001-0000001
estado | string | Estado del Documento Electrónico generado, pudiendo ser:<br>Aprobado<br>Aprobado con observación<br>Rechazado
respuesta_codigo | string | Código de la Respuesta de la SET
respuesta_mensaje | string | Mensaje de Respuesta de la SET
xml<br>(opcional) | string | El archivo **XML** generado del documento electronico.<br>Este elemento solamente se retorna cuando se le pasa el valor *true* en el atributo *xml* como **queryParam** al crear el DE o el LOTE, ej: <br>http://api.facturasend.com.py/&lt;tenantId&gt;/de/create?xml=true 
qr<br>(opcional) | string | El valor del  código **QR** generado del documento electronico.<br>Este elemento solamente se retorna cuando se le pasa el valor *true* en el atributo *qr* como **queryParam** al crear el DE o el LOTE, ej: <br>http://api.facturasend.com.py/&lt;tenantId&gt;/de/create?qr=true

En caso de errores, los atributos respuesta_codigo y respuesta_mensaje pueden ser utilizados para obtener más detalles sobre el error ocurrido. En caso de aprobación la respuesta_codigo retornará 0260. Los códigos de error se encuentran en el manual técnico.

# Consultas de la SET

## Consulta DE RUC

> Para consultar el DTE:

```shell
# Consulta los datos de una Empresa Física o Juridica por el RUC
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/ruc/80069563"  
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>"
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

axios.post(`https://api.facturasend.com.py/<tenantId>/ruc/80069563`, 
  null, 
  {headers}
)
.then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{
  "success": true,
  "respuesta_codigo": "0502",
  "respuesta_mensaje": "CDC encontrado",
  "razon_social": "TIPS S.A",
  "estado_codigo": "ACT",
  "estado_mensaje": "ACTIVO",
  "facturador_electronico": true
}
```
Este servicio consulta por el RUC la existencia de una Empresa directamente en el SIFEN, a travéz de la API del eKuatia.

El RUC informado como parámetro no debe contener el díto verificador.

Esta consulta por RUC también puede realizarse desde el panel de FacturaSend, todas las consultas anteriores realizadas quedan almacenadas y se despliegan en un listado.

Para invocar éste servicio se requiere que la empresa relacionada al tenant esté conectada a la SET, y también se requiere de un Certificado Digital válido.

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**ruc** | **Si** | RUC de la Empresa, sin el dígito verificador

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | true si la consulta se ejecutó con éxito, false si dio algún error
error | string | El mensaje de error en caso de que haya retornado success=false.
respuesta_codigo | string | Código de respuesta de la consulta.<br/>Valores: <br/><b>0500</b>=RUC no existe. <br/><b>0501</b>=RUC sin permiso consulta WS. <br/><b>0502</b>=RUC encontrado.
respuesta_mensaje | string | Mensaje de respuesta de la consulta. <br/>Valores: <br/><b>0500</b>=RUC no existe. <br/><b>0501</b>=RUC sin permiso consulta WS. <br/><b>0502</b>=RUC encontrado.
razon_social | string | Razón Social de la Empresa como se encuentra en el Marangatú.<br/><br/>Este atributo solo retorna si respuesta_codigo=0502
estado_codigo | string | Código del Estado o situación fiscal de la Empresa, con los posibles valores:<br/><b>ACT</b>=Activo<br/><b>SUS</b>=Suspensión Temporal<br/><b>SAD</b>=Suspensión Administrativa<br/><b>BLQ</b>=Bloqueado<br/><b>CAN</b>=Cancelado<br/><b>CDE</b>=Cancelado Definitivo<br/><br/>Este atributo solo retorna si respuesta_codigo=0502
estado_mensaje | string | Descripción del Estado o situación fiscal de la Empresa, con los posibles valores:<br/><b>ACT</b>=Activo<br/><b>SUS</b>=Suspensión Temporal<br/><b>SAD</b>=Suspensión Administrativa<br/><b>BLQ</b>=Bloqueado<br/><b>CAN</b>=Cancelado<br/><b>CDE</b>=Cancelado Definitivo<br/><br/>Este atributo solo retorna si respuesta_codigo=0502
facturador_electronico | boolean | true si la empresa ya se encuentra facturando electrónicamente.<br/><br/>Este atributo solo retorna si respuesta_codigo=0502

## Consulta DTE por CDC

> Para consultar el DTE:

```shell
# Consulta de un DTE por el Código de Control (CDC)
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/dte/cdc/01800695631001001000000612021112917595714694"  
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>"
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

axios.post(`https://api.facturasend.com.py/<tenantId>/dte/cdc/01800695631001001000000612021112917595714694`, 
  {headers}
)
.then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{
  "success": true,
  "fecha": "2022-01-22T12:07:48-03:00",
  "respuesta_codigo": "0422",
  "respuesta_mensaje": "CDC encontrado",
  "xml": "<xml? >...<rDE>",
  "protocolo": "93891821"
}
```
Este servicio consulta la existencia de un documento electrónico directamente en el SIFEN, a travéz de la API del eKuatia.

Esta consulta también puede realizarse desde el panel de FacturaSend, todas las consultas anteriores realizadas quedan almacenadas y se despliegan en un listado.

Para invocar éste servicio se requiere que la empresa relacionada al tenant esté conectada a la SET, y también se requiere de un Certificado Digital válido.


### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**cdc** | **Si** | Código CDC de 44 dígitos del Documento Electrónico

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | true si la consulta se ejecutó con éxito, false si dio algún error
error | string | El mensaje de error en caso de que haya retornado success=false.
deList | date-time | Fecha y hora de la consulta, ésta información es del servidor de eKuatia
respuesta_codigo | string | Código de respuesta de la consulta.<br/>Valores: <br/><b>0422</b>=CDC encontrado. <br/><b>0420</b>=CDC inexistente. <br/><b>0421</b>=RUC Certificado sin permiso
respuesta_mensaje | string | Mensaje de respuesta de la consulta. <br/>Valores: <br/>0422=<b>CDC encontrado.</b> <br/>0420=<b>CDC inexistente.</b> <br/>0421=<b>RUC Certificado sin permiso</b>
xml | string | Si la respuesta_codigo = 0422, entonces aqui se mostrará el XML obtenido desde el eKuatia.
protocolo | string | Si la respuesta_codigo = 0422, entonces aqui se mostrará el Protocolo de Autorización obtenido desde el eKuatia.

# Eventos del DE

## Evento de Cancelación
> Evento disponible para cancelar un Documento Electrónico que ya ha sido aprobado en la SET:

```shell
# Cancela un Documento electronico emitido
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/evento/cancelacion" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>" \
  --data-raw '{
    "cdc": "01800695631001001038720612021112917595714694",
    "motivo": "Se digito erroneamente la dirección del cliente"
  }'
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

const data = {
  "cdc": "01800695631001001038720612021112917595714694",
  "motivo": "Se digito erroneamente la dirección del cliente"
};

axios.post({
  url: `https://api.facturasend.com.py/<tenantId>/evento/cancelacion`,
  method: 'POST',
  {headers}
}
).then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{ "success" : true,
  "result" : {
    "ns2:rRetEnviEventoDe" : {
      "ns2:gResProcEVe" : "2022-02-08T14:39:00", 
      "ns2:gResProcEVe" : {
				"ns2:dEstRes" : "Aprobado",
				"ns2:gResProc" : {
          "ns2:dCodRes" : "",
					"ns2:dMsgRes" : ""
        }
      }
    }
			
  }
}
```
Este servicio ejecuta la cancelación de un documento específico teniendo como parámetro el valor de su CDC. 

Sólo podrá cancelar los documentos que hayan sido emitidos y aprobados dentro del plazo de 48 horas (2 dias).

Si el Documento Electrónico es cancelado de forma satisfactoria se enviará un email al cliente, avisando del evento junto con el documento electrónico cancelado. 

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**cdc** | **Si** | El CDC del Documento Electrónico que desea cancelar<br/>
**motivo** | **Si** | El motivo por el cual desea cancelar el documento<br/>

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | **true** si todo ocurrio bien y se canceló el Documento Electrónico, **false** si ocurrio algun error
result | object | Objeto resultante de la operación del evento, directamente en el formato que devuelve el eKuatia


## Evento de Inutilizacion
> Evento destinado para inutilizar las numeraciones del timbrado que no fueron utilizados, para dejar constancia de su no utilizacion en la SET:

```shell
# Cancela un Documento electronico emitido
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/evento/inutilizacion" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>" \
  --data-raw '{
        tipoDocumento: 1,
        establecimiento: `001`,
        punto: `001`,
        desde: 10,
        hasta: 12,
        motivo: `Se inutiliza la numeración por error de generacion en software`
    }'
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

const data = {
        tipoDocumento: 1,
        establecimiento: `001`,
        punto: `001`,
        desde: 10,
        hasta: 12,
        motivo: `Se inutiliza la numeración por error de generacion en software`
};

axios.post({
  url: `https://api.facturasend.com.py/<tenantId>/evento/inutilizacion`,
  method: 'POST',
  {headers}
}
).then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{ 
  "success" : true,
  "result" : {
    "ns2:rRetEnviEventoDe" : {
      "ns2:gResProcEVe" : "2022-02-08T14:39:00", 
      "ns2:gResProcEVe" : {
				"ns2:dEstRes" : "Aprobado",
				"ns2:gResProc" : {
          "ns2:dCodRes" : "",
					"ns2:dMsgRes" : ""
        }
      }
    }
  }
}
```
Este servicio ejecuta la inutilizacion de uno o mas numeraciones teniendo en cuenta el parametro desde y hasta incluyendo los valores limites especificados. 

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**tipoDocumento** | **Si** | Número entero que representa el Tipo de Documento Electronico del 1 al 7<br/>
**establecimiento** | **Si** | String conteniendo el valor del establecimiento que corresponde a la numeración que desea inutilizar<br/>
**punto** | **Si** | String conteniendo el valor del punto que corresponde a la numeración que desea inutilizar<br/>
**desde** | **Si** | Número inicial a partir del cual se deben inutilizar la numeración<br/>
**hasta** | **Si** | Número final hasta el cual se deben inutilizar la numeración<br/>
serie |No| Valor de la Serie del rango de números que se desean inutilizar<br/>
**motivo** | **Si** | El motivo por el cual desea inutilizar el rango de numeraciones<br/>

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | **true** si todo ocurrio bien y se inutilizaron las numeraciones del Timbrado, **false** si ocurrio algun error
result | object | Objeto resultante de la operación del evento, directamente en el formato que devuelve el eKuatia

## Evento de Conformidad
> Evento destinado para dar conformidad de recepcion de un Documento Electronico generado por un Emisor a su nombre o a nombre de su Empresa. Este evento no es obligatorio registrar:

```shell
# Cancela un Documento electronico emitido
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/evento/conformidad" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>" \
  --data-raw '{
    "cdc": "01800695631001001000000812021112910953738413",
    "tipoConformidad" : 1, //1-Parcial o 2-Total,
    "fechaRecepcion" : "2020-01-31T00:01:01"
  }'
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

const data = {
    "cdc": "01800695631001001000000812021112910953738413",
    "tipoConformidad" : 1, //1-Parcial o 2-Total,
    "fechaRecepcion" : "2020-01-31T00:01:01"
  };

axios.post({
  url: `https://api.facturasend.com.py/<tenantId>/evento/conformidad`,
  method: 'POST',
  {headers}
}
).then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{ "success" : true,
  "result" : {
    "ns2:rRetEnviEventoDe" : {
      "ns2:gResProcEVe" : "2022-02-08T14:39:00", 
      "ns2:gResProcEVe" : {
				"ns2:dEstRes" : "Aprobado",
				"ns2:gResProc" : {
          "ns2:dCodRes" : "",
					"ns2:dMsgRes" : ""
        }
      }
    }
			
  }
}
```
Con este evento se informa a la SET que el receptor se encuentra conforme total o parcialmente con el documento electronico recibido por parte de su Proveedor asi como tambien que ha recibido la mercaderia o servicio especificado en el documento. 

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**cdc** | **Si** | El CDC del Documento Electrónico que desea informar<br/>
**tipoConformidad** | **Si** | Valor numerico que indica si esta 1=Totalmente conforme o 2=Parcialmente conforme<br/>
**fechaRecepcion** | **Si** | Indica la fecha que ha recibido el documento electronico<br/>

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | **true** si todo ocurrio bien y se canceló el Documento Electrónico, **false** si ocurrio algun error
result | object | Objeto resultante de la operación del evento, directamente en el formato que devuelve el eKuatia

## Evento de Disconformidad
> Evento destinado para informar a la SET de una Disconformidad sobre un Documento Electronico recibido por parte de un tercero o un proveedor:

```shell
# Evento de disconformidad
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/evento/disconformidad" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>" \
  --data-raw '{
    "cdc": "01800695631001001038720612021112917595714694",
    "motivo": "Se genero erroneamente este documento a nuestro nombre"
  }'
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

const data = {
  "cdc": "01800695631001001038720612021112917595714694",
  "motivo": "Se genero erroneamente este documento a nuestro nombre"
};

axios.post({
  url: `https://api.facturasend.com.py/<tenantId>/evento/cancelacion`,
  method: 'POST',
  {headers}
}
).then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{ "success" : true,
  "result" : {
    "ns2:rRetEnviEventoDe" : {
      "ns2:gResProcEVe" : "2022-02-08T14:39:00", 
      "ns2:gResProcEVe" : {
				"ns2:dEstRes" : "Aprobado",
				"ns2:gResProc" : {
          "ns2:dCodRes" : "",
					"ns2:dMsgRes" : ""
        }
      }
    }
			
  }
}
```
Con este servicio usted deja constancia en la SET que el documento electronico tiene algun inconveniente o que no le corresponde haber recibido como empresa. 

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**cdc** | **Si** | El CDC del Documento Electrónico que desea informar<br/>
**motivo** | **Si** | El motivo por el cual esta disconforme con el documento<br/>

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | **true** si todo ocurrio bien y se canceló el Documento Electrónico, **false** si ocurrio algun error
result | object | Objeto resultante de la operación del evento, directamente en el formato que devuelve el eKuatia

## Evento de Desconocimiento
> Evento destinado para informar a la SET que usted no debio haber recibido dicho documento o que desconoce su origen y generacion:

```shell
# Informa a la SET de un Desconocimiento de un DTE
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/evento/desconocimiento" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>" \
  --data-raw '{
      "cdc": "01800695631001003000013712022010619364760029",    //DE o DTE
      "fechaEmision" : "2020-01-31T00:01:01",    //Fecha pasada
      "fechaRecepcion" : "2020-01-31T00:01:01",    //Fecha despues
      "tipoReceptor" : 1,
      "nombre" : "BRASIL CRESCENCIO",
      "ruc" : "50062360-0",
      "documentoTipo" : 11,
      "documentoNumero" : "",
      "motivo": "teste"
  }'
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

const data = {
  "cdc": "01800695631001003000013712022010619364760029",    //DE o DTE
  "fechaEmision" : "2020-01-31T00:01:01",    //Fecha pasada
  "fechaRecepcion" : "2020-01-31T00:01:01",    //Fecha despues
  "tipoReceptor" : 1,
  "nombre" : "BRASIL CRESCENCIO",
  "ruc" : "50062360-0",
  "documentoTipo" : 11,
  "documentoNumero" : "",
  "motivo": "teste"
};

axios.post({
  url: `https://api.facturasend.com.py/<tenantId>/evento/desconocimiento`,
  method: 'POST',
  {headers}
}
).then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{ "success" : true,
  "result" : {
    "ns2:rRetEnviEventoDe" : {
      "ns2:gResProcEVe" : "2022-02-08T14:39:00", 
      "ns2:gResProcEVe" : {
				"ns2:dEstRes" : "Aprobado",
				"ns2:gResProc" : {
          "ns2:dCodRes" : "",
					"ns2:dMsgRes" : ""
        }
      }
    }
			
  }
}
```
Este servicio informa a la SET que usted desconoce un determinado documento electronico y que ha sido generado erroneamente a su nombre o a su empresa. 

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**cdc** | **Si** | El CDC del Documento Electrónico que desea informar<br/>
**fechaEmision** | **Si** | Fecha de emision del Documento Electronico
**fechaRecepcion** | **Si** | Fecha de recepcion del documento electronico
**tipoReceptor** | **Si** | Tipo de Receptor
**nombre** | **Si** | Nombre del Receptor
**ruc** | **Si** | RUC del Receptor con el digito verificador
**documentoTipo** | **Si** | Tipo de Documento
**documentoNumero** | **Si** | Numero de documento
**motivo** | **Si** | El motivo por el cual desea cancelar el documento<br/>

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | **true** si todo ocurrio bien y se canceló el Documento Electrónico, **false** si ocurrio algun error
result | object | Objeto resultante de la operación del evento, directamente en el formato que devuelve el eKuatia

## Evento de Notificación
Evento destinado para informar a la SET que conoce dicho documento, sin embargo, aún no tiene condiciones para manifestarse de forma conclusiva (con Conformidad, Disconformidad o Desconocimiento). 

Es un evento opcional.

```shell
# Notifica a la SET de que se ha recepcionado un DTE
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/evento/notificacion" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>" \
  --data-raw '{
      "cdc": "01800695631001003000013712022010619364760029",    //DE o DTE
      "fechaEmision" : "2020-01-31T00:01:01",    //Fecha pasada
      "fechaRecepcion" : "2020-01-31T00:01:01",    //Fecha despues
      "tipoReceptor" : 1,
      "nombre" : "BRASIL CRESCENCIO",
      "ruc" : "50062360-0",
      "documentoTipo" : 11,
      "documentoNumero" : "",
      "totalPYG": "150000"
  }'
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

const data = {
  "cdc": "01800695631001003000013712022010619364760029",    //DE o DTE
  "fechaEmision" : "2020-01-31T00:01:01",    //Fecha pasada
  "fechaRecepcion" : "2020-01-31T00:01:01",    //Fecha despues
  "tipoReceptor" : 1,
  "nombre" : "BRASIL CRESCENCIO",
  "ruc" : "50062360-0",
  "documentoTipo" : 11,
  "documentoNumero" : "",
  "totalPYG": "150000"
};

axios.post({
  url: `https://api.facturasend.com.py/<tenantId>/evento/notificacion`,
  method: 'POST',
  {headers}
}
).then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{ "success" : true,
  "result" : {
    "ns2:rRetEnviEventoDe" : {
      "ns2:gResProcEVe" : "2022-02-08T14:39:00", 
      "ns2:gResProcEVe" : {
				"ns2:dEstRes" : "Aprobado",
				"ns2:gResProc" : {
          "ns2:dCodRes" : "",
					"ns2:dMsgRes" : ""
        }
      }
    }
			
  }
}
```
Este servicio informa a la SET que usted desconoce un determinado documento electronico y que ha sido generado erroneamente a su nombre o a su empresa. 

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**cdc** | **Si** | El CDC del Documento Electrónico que desea informar<br/>
**fechaEmision** | **Si** | Fecha de emision del Documento Electronico
**fechaRecepcion** | **Si** | Fecha de recepcion del documento electronico
**tipoReceptor** | **Si** | Tipo de Receptor
**nombre** | **Si** | Nombre del Receptor
**ruc** | **Si** | RUC del Receptor con el digito verificador
**documentoTipo** | **Si** | Tipo de Documento
**documentoNumero** | **Si** | Numero de documento
**totalPYG** | **Si** | Monto total del documento en GS<br/>

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | **true** si todo ocurrio bien y se canceló el Documento Electrónico, **false** si ocurrio algun error
result | object | Objeto resultante de la operación del evento, directamente en el formato que devuelve el eKuatia

## Evento de Nominación
Evento destinado para informar a la SET el receptor de una factura, cuando la factura originalmente fue hecha a un innominado. 

Es un evento que depende de la necesidad del emisor, a menudo cuando necesita realizar una nota de crédito sobre una factura que originalmente se generó a un innominado.

```shell
# Invoca el evento de nominación
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/evento/nominacion" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>" \
  --data-raw '{
        "cdc": `01800695631001002100700812022063013102931279`,  // DTE
        "motivo": `Se asignar el receptor correcto del DTE`,
        "contribuyente" : true,
        "ruc" : "2005001-1",
        "razonSocial" : "Marcos Adrian Jara Rodriguez",
        "nombreFantasia" : "Marcos Adrian Jara Rodriguez",
        "tipoOperacion" : 1,
        "direccion" : "Avda Calle Segunda y Proyectada",
        "numeroCasa" : "1515",
        "departamento" : 11,
        "departamentoDescripcion" : "ALTO PARANA",
        "distrito" : 143,
        "distritoDescripcion" : "DOMINGO MARTINEZ DE IRALA",
        "ciudad" : 3344,
        "ciudadDescripcion" : "PASO ITA (INDIGENA)",
        "pais" : "PRY",
        "paisDescripcion" : "Paraguay",
        "tipoContribuyente" : 1,
        "telefono" : "061874874",
        "celular" : "595976254125",
        "email" : "cliente@cliente.com",
        "codigo" : "1548"
  }'
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

const data = {
  "cdc": `01800695631001002100700812022063013102931279`,  // DTE
  "motivo": `Se asignar el receptor correcto del DTE`,
  "contribuyente" : true,
  "ruc" : "2005001-1",
  "razonSocial" : "Marcos Adrian Jara Rodriguez",
  "nombreFantasia" : "Marcos Adrian Jara Rodriguez",
  "tipoOperacion" : 1,
  "direccion" : "Avda Calle Segunda y Proyectada",
  "numeroCasa" : "1515",
  "departamento" : 11,
  "departamentoDescripcion" : "ALTO PARANA",
  "distrito" : 143,
  "distritoDescripcion" : "DOMINGO MARTINEZ DE IRALA",
  "ciudad" : 3344,
  "ciudadDescripcion" : "PASO ITA (INDIGENA)",
  "pais" : "PRY",
  "paisDescripcion" : "Paraguay",
  "tipoContribuyente" : 1,
  "telefono" : "061874874",
  "celular" : "595976254125",
  "email" : "cliente@cliente.com",
  "codigo" : "1548"
};

axios.post({
  url: `https://api.facturasend.com.py/<tenantId>/evento/nominacion`,
  method: 'POST',
  {headers}
}
).then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{ "success" : true,
  "result" : {
    "ns2:rRetEnviEventoDe" : {
      "ns2:gResProcEVe" : "2022-02-08T14:39:00", 
      "ns2:gResProcEVe" : {
				"ns2:dEstRes" : "Aprobado",
				"ns2:gResProc" : {
          "ns2:dCodRes" : "",
					"ns2:dMsgRes" : ""
        }
      }
    }
			
  }
}
```
Tenga en cuenta los parametros para enviar el evento. 

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**cdc** | **Si** | El CDC del Documento Electrónico que desea nominar. Debe existir en Facturasend<br/>
**motivo** | **Si** | El motivo del evento de nominación
**contribuyente** | **Si** | Campo booleano que indica si el nominado es o no un contribuyente
ruc |No| RUC del Receptor con el digito verificador. Obligatorio si el nominado es un contribuyente.
**razonSocial** | **Si** | Nombre o Razón Social del Receptor
nombreFantasia |No| Nombre de Fantasía del Receptor
**tipoOperacion** | **Si** | Tipo de Operación del Receptor, siendo: 1-B2B, 2-B2C, 4-B2F
direccion |No| Dirección del Receptor. Obligatorio si tipoOperacion=4
numeroCasa |No| Número de Casa del Receptor. Obligatorio si se pasa la dirección. Cuando es contribuyente debe corresponder a lo declarado en el RUC
departamento|No| Código del departamento,Campo obligatorio si se informa la dirección y tipoOperacion ≠ 4, no se debe informar cuando tipoOperacion = 4.
distrito|No|Código del distrito del Cliente, El  código debe seguir la Tabla 2.1 – Distritos del Manual Tecnico.
ciudad|No|Código de la ciudad del Cliente. Campo obligatorio si se informa la dirección y tipoOperacion≠4, no se debe informar cuando tipoOperacion = 4.
**pais**|**Si**|Código del Pais del Cliente, Segun XSD de Codificación de Países
tipoContribuyente |No| Tipo de contribuyente Ej.: 1= Persona Física, 2= Persona Jurídica<br/>Obligatorio si contribuyente = true, No informar si contribuyente = false
documentoTipo |No| Tipo de documento del cliente, de acuerdo a <br/><br/>1=Cédula paraguaya<br/>2=Pasaporte<br/>3=Cédula extranjera<br/>4=Carnet de residencia<br/>5=Tarjeta Diplomática de exoneración fiscal<br/>9=Otro (informar data.documentoTipoDescripcion). Obligatorio si data.contribuyente = false
documentoNumero |No| Número de documento de identidad. Obligatorio si data.contribuyente = false
telefono |No| Número de teléfono. Debe incluir el prefijo de la ciudad si pais = PRY
celular | No | Numero de celular del cliente
email |No| Correo electronico del cliente<br/><br/>Si se le pasa más de un correo (separado por comas) en eKuatia se incluirá sólo el primero
codigo |No| Código del Cliente

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | **true** si todo ocurrio bien y se nominó el Documento Electrónico, **false** si ocurrio algun error
result | object | Objeto resultante de la operación del evento, directamente en el formato que devuelve el eKuatia



# Lote en Borrador
Un lote puede ser enviado como borrador a FacturaSend, indicando el parametro de consulta **draft=true**, al crear el Lote.

Un lote en borrador no se envia a la SET hasta que se envie un comando de Confirmación. 

Esta opción es muy util para simular el comportamiento completo de un envio de lote, como asi también el flujo que sigue dentro de su sistema, asi como también para poder visualizar el KUDE y estar seguro de sus datos, antes de enviar a la SET.

Un lote en borrador puede ser CONFIRMADO o DESCARTADO, Si se Confirma, entonces se da la señal para que este lote se envie a la SET y si se Descarta nunca se envia ese Lote a la SET.

## Confirmar un Lote en Borrador

> Para confirmar un Lote en Borrador:

```shell
# Confirma un Lote que ha sido enviado anteriormente como un borrador.
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/lote/draft-confirm/<loteId>"  
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>"
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

axios.post(`https://api.facturasend.com.py/<tenantId>/lote/draft-confirm/<loteId>`, 
  null, 
  {headers}
)
.then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{
  "success": true
}
```
Este servicio confirma un lote que habia sido enviado originalmente como borrador a FacturaSend, procesandolo y enviandolo a la SET para su proceso.

Debe tener en cuenta que un lote en borrador no puede ser confirmado despues de las 72hs. de su creación, por motivo de la Firma Digital.

### Parámetros (QueryParam)
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**loteId** | **Si** | El Id del lote que desea confirmar

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | true si la confirmación se ejecutó con éxito, false si dio algún error
error | string | El mensaje de error en caso de que haya retornado success=false.

## Rechazar un Lote en Borrador

> Para rechazar un Lote en Borrador:

```shell
# Rechazar un Lote que ha sido enviado anteriormente como un borrador.
curl \
  -X \
  POST "https://api.facturasend.com.py/<tenantId>/lote/draft-reject/<loteId>"  
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>"
```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

axios.post(`https://api.facturasend.com.py/<tenantId>/lote/draft-reject/<loteId>`, 
  null, 
  {headers}
)
.then( respuesta => {
  console.log(respuesta);
});
```

Este servicio rechaza/descarta un lote que habia sido enviado originalmente como borrador a FacturaSend, no enviandolo finalmente a la SET y de esta forma dando por cerrado al envio de lote.

### Parámetros
Parámetro | Requerido | Descripción
--------- | --------- | -----------
**loteId** | **Si** | El Id del lote que desea confirmar

### Respuesta
Atributo | Tipo | Descripción
--------- | --------- | -----------
success | boolean | true si la consulta se ejecutó con éxito, false si dio algún error
error | string | El mensaje de error en caso de que haya retornado success=false.







# Otros servicios
A continuación se presentan otros servicios que pueden ser invocados desde FacturaSend

## Consulta de Departamentos
Servicio que obtiene la lista de todos los departamentos del Paraguay admitidos por el SIFEN. En cada elemento se recupera el código y la descripción del Departamento.

```shell
# Obtiene los departamentos
curl \
  GET "https://api.facturasend.com.py/<tenantId>/departamentos" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>" 

```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

axios.post({
  url: `https://api.facturasend.com.py/<tenantId>/departamentos`,
  method: 'GET',
  {headers}
}
).then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{ 
  "success" : true,
  "result" : [{
      "codigo": 17,
      "descripcion": "ALTO PARAGUAY"
    },
    {
      "codigo": 11,
      "descripcion": "ALTO PARANA"
    },
    {
      "codigo": 99,
      "descripcion": "OTROS"
    }]
}
```
Puede utilizar este servicio para mantener actualizado los datos de los departamentos en su Sistema. 

## Consulta de Distritos

Servicio que obtiene la lista de todos los distritos del Paraguay admitidos por el SIFEN. En cada elemento se recupera el código y la descripción, y el Departamento al cual pertenece el Distrito.

Puede especificar un departamento específico del cual desea obtener los distritos, en la ruta /<departamentoId>/ de la URL, o puede especificar en dicho campo el valor NULL si desea recuperar todos los distritos.

También es posible realizar busquedas por nombres de distritos parecidos enviando un parámetro ?nombre=, indicando el valor para el filtro. 

```shell
# Obtiene los distritos del departamento y filtrando por el nombre
curl \
  GET "https://api.facturasend.com.py/<tenantId>/distritos/<departamentoId>?nombre=bahia" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>" 

```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

axios.post({
  url: `https://api.facturasend.com.py/<tenantId>/distritos/<departamentoId>?nombre=bahia`,
  method: 'GET',
  {headers}
}
).then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{ 
  "success" : true,
  "result" : [{
    "codigo": 196,
    "descripcion": "BAHIA NEGRA",
    "departamento": {
        "codigo": 17,
        "descripcion": "ALTO PARAGUAY"
    }
  }]
}
```
Puede utilizar este servicio para mantener actualizado los datos de los distritos en su Sistema. 

## Consulta de Ciudades

Servicio que obtiene la lista de todas las ciudades del Paraguay admitidos por el SIFEN. En cada elemento se recupera el código y la descripción, y el objeto Distrito al cual pertenece la Ciudad.

Puede especificar un distrito específico del cual desea obtener las ciudades, en la ruta /<distritoId>/ de la URL, o puede especificar en dicho campo el valor NULL si desea recuperar todos las Ciudades.

También es posible realizar busquedas por nombres de ciudades parecidos enviando un parámetro ?nombre=, indicando el valor para el filtro. 

```shell
# Obtiene los distritos del departamento y filtrando por el nombre
curl \
  GET "https://api.facturasend.com.py/<tenantId>/ciudades/<distritoId>?nombre=asuncion" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>" 

```

```javascript
# El ejemplo se muestra utilizando AXIOS
import axios from 'axios';

const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

axios.post({
  url: `https://api.facturasend.com.py/<tenantId>/ciudades/<distritoId>?nombre=asuncion`,
  method: 'GET',
  {headers}
}
).then( respuesta => {
  console.log(respuesta);
});
```

> Como respuesta obtendrá lo siguiente:

```json
{ 
  "success" : true,
  "result" : [{
      "codigo": 5666,
      "descripcion": "B.AEREA NVA.ASUNCION (PICUIBA)",
      "distrito": {
          "codigo": 234,
          "descripcion": "GRAL. EUGENIO A. GARAY",
          "departamento": {
              "codigo": 16,
              "descripcion": "BOQUERON"
          }
      }
    }, {
      "codigo": 5678,
      "descripcion": "NUEVA ASUNCION",
      "distrito": {
          "codigo": 234,
          "descripcion": "GRAL. EUGENIO A. GARAY",
          "departamento": {
              "codigo": 16,
              "descripcion": "BOQUERON"
          }
      }
    }, {
      "codigo": 999,
      "descripcion": "Otros",
      "distrito": {
          "codigo": 999,
          "descripcion": "Otros",
          "departamento": {
              "codigo": 999,
              "descripcion": "Otros"
          }
      }
    }]
}
```
Puede utilizar este servicio para mantener actualizado los datos de los distritos en su Sistema. 

# Glosario

Parameter | Description
--------- | -----------
DE | Documento Electrónico
DTE | Documento Tributario Electrónico
