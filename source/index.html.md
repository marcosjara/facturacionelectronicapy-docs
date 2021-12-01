---
title: Referencia de la API - FacturaSend

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  - <a href='#'>FacturaSend Login</a>
  - <a href='https://www.facturasend.com.py'>Inicio de FacturaSend</a>

includes:
  - errors

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
3. Generación de la URL del Codigo QR dentro del documento XML.
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

axios.get(`https://api.facturasend.com.py/<tenantId>/test`)
.then( respuesta => {
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

# Lotes

## Envio de lotes

```shell
curl -X POST "http://api.facturasend.com.py/<tokenId>/lote/create" \
  -H "Authorization: Bearer api_key_<hdiweuw-92jwwle...>"
```

```javascript
import axios from 'axios';
const data = {
  datos_de_la_peticion...
};
const headers = {
  `Authorization` : `Bearer api_key_<hdiweuw-92jwwle...>`
};

axios.post(`https://api.facturasend.com.py/<tokenId>/lote`, 
          data, 
          {headers})
.then( respuesta => {
  console.log(respuesta);
});
```

Esta invocación, crea los documentos electrónicos y los envía a la SET.

### Petición HTTP

`POST http://api.facturasend.com.py/<tokenId>/lote/create`

> La petición requiere de la siguiente estructura de Datos JSON:

```json
[
  {
    "tipoDocumento" : 1,
    "establecimiento" : 1,
    "punto" : "001",
    "numero" : 4, 
    "descripcion" : "Aparece en el documento",
    "observacion" : "Cualquier informacion de interes",
    "tipoContribuyente" : 1,
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
        "telefono" : "xyz",
        "celular" : "xyz",
        "email" : "cliente@cliente.com",
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
                "numeroTarjeta": 3232,
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
        "observacion": "Cualquier informacion de interes", 
        "partidaArancelaria" : 4444,
        "ncm": "123456",
        "unidadMedida": 77,
        "cantidad": 10.5,
        "precioUnitario": 10800,
        "cambio": 0.0,
        "descuento": 0,
        "descuentoPorcentaje": 0,
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
        "importador" : {
            "nombre" : "Importadora Parana S.A.",
            "direccion" : "Importadora Parana S.A.",
            "registroImportador" : "Importadora Parana S.A.",
            "registroSenave" : "Importadora Parana S.A.",
            "registroEntidadComercial" : "Importadora Parana S.A."
        },
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
    "detalleTransporte" : {
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
            "telefonoContacto" : "097x"
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
            "telefonoContacto" : "097x"
        },
        "vehiculo" : {
            "tipo" : "Camioneta",
            "marca" : "Nissan",
            "documentoTipo" : 1, 
            "documentoNumero" : "232323-1",
            "obs" : "",
            "numeroMatricula" : "ALTO PARANA",
            "numeroVuelo" : "32123"
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
]
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


### Parametros del objeto principal o data

Para los atributos del objeto JSON también puede utilizar **_ (underscore)**, es decir, se interpreta de la misma manera si envia *tipoDocumento* o *tipo_documento*. 

Parámetro | Requerido | Descripción
--------- | --------- | -----------
**tipoDocumento** | **Si** | Uno de los 5 tipos de documentos admitidos por la SET (1, 4, 5, 6, 7). Ej.:<br/>1= Factura electrónica, <br/>4= Autofactura electrónica <br/>5= Nota de crédito electrónica, <br/>6= Nota de débito electrónica, <br/>7= Nota de remisión electrónica. <br/><br/>**Campo XML:** C002 
**ruc** | **Si** | RUC del contribuyente emisor(empresa). Este campo debe ir con el digito verificador Ej.: 80069563-1
**establecimiento**|**Si**| Son los 3 primeros digitos de la factura, Se puede enviar 1 o 001 <br/>**Campo XML:** C005 
**punto**|**Si**| Es la segunda parte de una factura.  Ej.: 001.<br/>**Campo XML:** C006 
**numero**|**Si**| Es la parte final de la factura, se puede enviar directamente el numero o completar con 0 hasta obtener 7 digitos. C007 Ej.: 0000001, 1.
descripcion|No| Información de interés del Fisco respecto al DE.<br/>**Campo XML:** B006.
observacion|No| Información de interés del emisor respecto al DE.<br/>**Campo XML:** B005.
**fecha**|**Si**| Fecha y hora de emisión del DE. <br/>**Campo XML:** D002.
**tipoEmision**|**Si**| Tipo de emisión (1,2) Ej: 1= Normal, 2= Contingencia. <br/>**Campo XML:** B002.
tipoTransaccion|No|Obligatorio si tipoDocumento= 2 o 4.	<br/>Ej.: 1= Venta de mercadería, 2= Prestación de servicios <br/>**Campo XML:** D011
**tipoImpuesto**|**Si**|Tipo de impuesto afectado, Fijo 1 para venta.(1= IVA, 2= ISC, 3=Renta, 4=Ninguno, 5=IVA - Renta) <br/>**Campo XML:**  D013
**moneda**|**Si**|Descripcion de la moneda de acuerdo con la norma ISO 4217 Ej.: "PYG" D015
condicionAnticipo|No|Condición del Anticipo,  Ej.:(1= Anticipo Global,2= Anticipo por ítem)no es obligatorio informar. <br/>**Campo XML:** D019
condicionTipoCambio|No|Condición del tipo de cambio.Obligatorio si moneda ≠ PYG, null para PYG <br/>**Campo XML:** D017
cambio|No|Tipo de cambio de la operación. null para PYG o el cambio del día de la moneda de venta. <br/>**Campo XML:** D018
cliente|Si|Datos del Receptor del Documento Electrónico. Ver detalle en tabla siguiente.<br/>

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
departamento|No| Codigo del departamento,Campo obligatorio si se informa la direccion y tipoOperacion ≠ 4, no se debe informar cuando tipoOperacion = 4.<br/>**Campo XML:** D219 
distrito|No|Codigo del distrito del Cliente, El codigo debe seguir la Tabla 2.1 – Distritos del Manual Tecnico. <br/>**Campo XML:** D221
ciudad|No|Codigo de la ciudad del Cliente. Campo obligatorio si se informa la direccion y tipoOperacion≠4, no se debe informar cuando tipoOperacion = 4.<br/>**Campo XML:**D223
**pais**|**Si**|Codigo del Pais del Cliente, Segun XSD de Codificación de Países<br/>**Campo XML:**D203
tipoContribuyente|No|Tipo de contribuyente Ej.: 1= Persona Física, 2= Persona Jurídica<br/>Obligatorio si contribuyente = true, No informar si contribuyente = false<br/>**Campo XML:**D205
documentoTipo|No|Tipo de documento del cliente <br/>**Campo XML:**D208
documentoNumero|No|Número de documento de identidad.Obligatorio si contribuyente = false y tipoOperacion ≠ 4.<br/>En caso de DE innominado, completar con 0 (cero)<br/>**Campo XML:**D210
telefono|No|Número de teléfono. Debe incluir el prefijo de la ciudad si pais = PRY<br/>**Campo XML:**D214
celular|No|Numero de celular del cliente <br/>**Campo XML:**D215
email|No|Correo electronico del cliente<br/>**Campo XML:**D216
codigo|No|Codigo del Cliente<br/>**Campo XML:**D217

### Parametro del objeto data.items

Parámetro | Requerido | Descripción
--------- | --------- | -----------
**codigo** |**Si**|Código interno de identificación de la mercadería o servicio de responsabilidad del emisor<br/>**Campo XML:**E701 
**descripcion**|**Si** |Descripción del producto y/o servicio. Equivalente a nombre del producto establecido en la RG 24/2019<br/>**Campo XML:**E708
observacion|No|Informacion de intetes acerca del item<br/>**Campo XML:**E714
partidaArancelaria|No|Partida arancelaria<br/>**Campo XML:**E702
ncm|No|Nomenclatura común del Mercosur (NCM)<br/>**Campo XML:**E703
**unidadMedida**|**Si**|Es la unidad de medida del producto <br/>**Campo XML:**E709
**cantidad**|**Si**|Cantidad del producto y/o servicio <br/>**Campo XML:**E711
**precioUnitario**|**Si**|Precio unitario del producto y/o servicio (incluidos impuestos)<br/>**Campo XML:**E721
cambio|No|Tipo de cambio por ítem<br/>**Campo XML:**E725
descuento|No|Descuento particular sobre el precio unitario por ítem (incluidos impuestos)<br/>**Campo XML:**EA002
descuentoPorcentaje|No|Porcentaje de descuento particular por ítem<br/>**Campo XML:**EA003
anticipo|No|Anticipo particular sobre el precio unitario por ítem (incluidos impuestos)<br/>**Campo XML:**EA006
subtotal||<br/>**Campo XML:**
pais|No|<br/>Código del país de origen del producto**Campo XML:**E712
paisDescripcion|No|Nombre del país de origen del producto<br/>**Campo XML:**E713
tolerancia|No|Código de datos de relevancia de los productos<br/>**Campo XML:**E715
toleranciaCantidad|No|Cantidad de quiebra o merma<br/>**Campo XML:**E717
toleranciaPorcentaje|No|Porcentaje de quiebra o merma<br/>**Campo XML:**E718
cdcAnticipo|No|CDC del anticipo<br/>**Campo XML:**E719

### Validaciones

- Todos los documentos que se envían utilizando éste método, deben ser del mismo tipo, por ejemplo todos ellos factura electrónica.
- Puede enviar como mínimo 1 documento y como máximo 50 por llamada, si tienen más debe realizarlo en una siguiente llamada.


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
```http://localhost:4567/#autorizacion

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

