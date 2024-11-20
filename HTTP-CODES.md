**Codigos de respuesta HTTP** 

**1xx: Respuestas Informativas** 

<p align="justify">Petición recibida, continuando proceso. Esta respuesta significa que el servidor ha recibido los encabezados de la petición, y que el cliente debería proceder a enviar el cuerpo de la misma (en el caso de peticiones para las cuales el cuerpo necesita ser enviado; por ejemplo, una petición Hypertext Transfer Protocol). Si el cuerpo de la petición es largo, es ineficiente enviarlo a un servidor, cuando la petición ha sido ya rechazada, debido a encabezados inapropiados. Para hacer que un servidor cheque si la petición podría ser aceptada basada únicamente en los encabezados de la petición, el cliente debe enviar Expect: 100-continue como un encabezado en su petición inicial (vea Plantilla:Web-RFC: Expect header) y verificar si un código de estado 100 Continue es recibido en respuesta, antes de continuar (o recibir 417 Expectation Failed y no continuar)</p>

**100 - Continue**
<p align="justify">El navegador puede continuar realizando su petición (se utiliza para indicar que la primera parte de la petición del navegador se ha recibido correctamente)</p>

**101 - Switching Protocols**
<p align="justify">El servidor acepta el cambio de protocolo propuesto por el navegador (puede ser por ejemplo un cambio de HTTP 1.0 a HTTP 1.1)</p>

**102 - Processing (WebDAV - RFC 2518)**
<p align="justify">El servidor está procesando la petición del navegador pero todavía no ha terminado (esto evita  que el  navegador  piense  que  la  petición  se ha perdido  cuando no  recibe  ninguna respuesta)</p>

**103 - Checkpoint**
<p align="justify">Se va a reanudar una petición POST o PUT que fue abortada previamente.2</p>

**2xx: Peticiones correctas**
<p align="justify">Esta clase de código de estado indica que la petición fue recibida correctamente, entendida y aceptada.</p>

**200 - OK** 
Respuesta estándar para peticiones correctas. 

**201 - Created**
<p align="justify">La petición ha sido completada y ha resultado en la creación de un nuevo recurso.</p>

**202 - Accepted**
<p align="justify">La petición ha sido aceptada para procesamiento, pero este no ha sido completado. La petición eventualmente pudiere no ser satisfecha, ya que podría ser no permitida o prohibida cuando el procesamiento tenga lugar.</p>

**203 - Non-Authoritative Information (desde HTTP/1.1)**
<p align="justify">La petición se ha completado con éxito, pero su contenido no se ha obtenido de la fuente originalmente solicitada sino de otro servidor</p>

**204 - No Content**
<p align="justify">La petición se ha completado con éxito pero su respuesta no tiene ningún contenido (la respuesta sí que puede incluir información en sus cabeceras HTTP)</p>

**205 - Reset Content**
<p align="justify">La petición se ha completado con éxito, pero su respuesta no tiene contenidos y además, el navegador tiene que inicializar la página desde la que se realizó la petición (este código es útil por ejemplo para páginas con formularios cuyo contenido debe borrarse después de que el usuario lo envíe)</p>

**206 - Partial Content**
<p align="justify">La petición servirá parcialmente el contenido solicitado. Esta característica es utilizada por herramientas  de  descarga  como  wget  para  continuar  la  transferencia  de  descargas anteriormente  interrumpidas,  o  para  dividir  una  descarga  y  procesar  las  partes simultáneamente.</p>

**207 - Multi-Status (Multi-Status, WebDAV)**
<p align="justify">El cuerpo del mensaje que sigue es un mensaje XML y puede contener algún número de códigos de respuesta separados, dependiendo de cuántas sub-peticiones sean hechas.</p>

**208 - Already Reported (WebDAV)**
<p align="justify">El listado de elementos DAV ya se notificó previamente, por lo que no se van a volver a listar.</p>

**3xx: Redirecciones**
El cliente tiene que tomar una acción adicional para completar la petición. 

<p align="justify">Esta clase de código de estado indica que una acción subsecuente necesita efectuarse por el agente de usuario para completar la petición. La acción requerida puede ser llevada a cabo por el agente de usuario sin interacción con el usuario si y solo si el método utilizado en la segunda petición es GET o HEAD. El agente de usuario no debe redirigir automáticamente una  petición  más  de  5  veces,  dado  que  tal  funcionamiento  indica  usualmente  un  Bucle infinito.</p>

**300 - Multiple Choices**
<p align="justify">Indica opciones múltiples para el URI que el cliente podría seguir. Esto podría ser utilizado, por ejemplo, para presentar distintas opciones de formato para video, listar archivos con distintas extensiones o word sense disambiguation.</p>

**301 - Moved Permanently**
<p align="justify">Esta y todas las peticiones futuras deberían ser dirigidas a la URI dada.</p>

**302 - Found**
<p align="justify">Este es el código de redirección más popular, pero también un ejemplo de las prácticas de la industria contradiciendo el estándar. La especificación HTTP/1.0 (RFC 1945) requería que el cliente  realizara  una  redirección  temporal  (la  frase  descriptiva  original  fue  "Moved Temporarily"), pero los navegadores populares lo implementaron como 303 See Other. Por tanto, HTTP/1.1 añadió códigos de estado 303 y 307 para eliminar la ambigüedad entre ambos  comportamientos.  Sin  embargo,  la  mayoría  de  aplicaciones  web  y  bibliotecas  de desarrollo aún utilizan el código de respuesta 302 como si fuera el 303.</p>

**303 - See Other (desde HTTP/1.1)**
<p align="justify">La respuesta a la petición puede ser encontrada bajo otra URI utilizando el método GET.</p>

**304 - Not Modified**
<p align="justify">Indica que la petición a la URL no ha sido modificada desde que fue requerida por última vez. Típicamente, el cliente HTTP provee un encabezado como If-Modified-Since para indicar una fecha y hora contra la cual el servidor pueda comparar. El uso de este encabezado ahorra ancho de banda y reprocesamiento tanto del servidor como del cliente.</p>

**305 - Use Proxy (desde HTTP/1.1)**
<p align="justify">Muchos clientes HTTP (como Mozilla3 e Internet Explorer) no se apegan al estándar al procesar respuestas con este código, principalmente por motivos de seguridad.</p>

**306 - Switch Proxy**
<p align="justify">Este código se utilizaba en las versiones antiguas de HTTP pero ya no se usa (aunque está reservado para usos futuros)</p> 

**307 - Temporary Redirect (desde HTTP/1.1)**
<p align="justify">Se trata de una redirección que debería haber sido hecha con otra URI, sin embargo aún puede ser procesada con la URI proporcionada. En contraste con el código 303, el método de la petición no debería ser cambiado cuando el cliente repita la solicitud. Por ejemplo, una solicitud POST tiene que ser repetida utilizando otra petición POST.</p>

**308 - Permanent Redirect**
<p align="justify">El  recurso  solicitado  por  el  navegador  se  encuentra  en  otro  lugar  y  este  cambio  es permanente. A diferencia del código 301, no se permite cambiar el método HTTP para la nueva petición (así por ejemplo, si envías un formulario a un recurso que ha cambiado de lugar, todo seguirá funcionando bien)</p>

**4xx Errores del cliente**
La solicitud contiene sintaxis incorrecta o no puede procesarse. 

<p align="justify">La intención de la clase de códigos de respuesta 4xx es para casos en los cuales el cliente parece  haber  errado  la  petición.  Excepto  cuando  se  responde  a  una  petición  HEAD,  el servidor debe incluir una entidad que contenga una explicación a la situación de error, y si es una condición temporal o permanente. Estos códigos de estado son aplicables a cualquier método de solicitud (como GET o POST). Los agentes de usuario deben desplegar cualquier entidad  al  usuario.  Estos  son  típicamente  los  códigos  de  respuesta  de  error  más comúnmente encontrados.</p>

**400 - Bad Request**
<p align="justify">La solicitud contiene sintaxis errónea y no debería repetirse.</p>

**401 - Unauthorized**
<p align="justify">Similar al 403 Forbidden, pero específicamente para su uso cuando la autentificación es posible pero ha fallado o aún no ha sido provista. Vea autentificación HTTP básica y Digest access authentication.</p>

**402 - Payment Required**
<p align="justify">La intención original era que este código pudiese ser usado como parte de alguna forma o esquema de Dinero electrónico o micropagos, pero eso no sucedió, y este código nunca se utilizó.</p>

**403 - Forbidden** 
<p align="justify">La solicitud fue legal, pero el servidor rehúsa responderla dado que el cliente no tiene los privilegios para hacerla. En contraste a una respuesta 401 No autorizado, la autenticación no haría la diferencia.</p>

**404 - Not Found** 
<p align="justify">Recurso  no  encontrado.  Se  utiliza  cuando  el  servidor  web  no  encuentra  la  página  o recurso solicitado.</p> 

**405 - Method Not Allowed** 
<p align="justify">Una petición fue hecha a una URI utilizando un método de solicitud no soportado por dicha URI; por ejemplo, cuando se utiliza GET en una forma que requiere que los datos sean presentados vía POST, o utilizando PUT en un recurso de solo lectura.</p>

**406 - Not Acceptable**
<p align="justify">El servidor no es capaz de devolver los datos en ninguno de los formatos aceptados por el cliente, indicados por éste en la cabecera "Accept" de la petición.</p>

**407 - Proxy Authentication Required**

**408 - Request Timeout**
<p align="justify">El cliente falló al continuar la petición - excepto durante la ejecución de videos Adobe Flash cuando solo significa que el usuario cerró la ventana de video o se movió a otro. Ref</p>

**409 - Conflict** 
<p align="justify">Indica que la solicitud no pudo ser procesada debido a un conflicto con el estado actual del recurso que esta identifica.</p>

**410 - Gone**
<p align="justify">Indica que el recurso solicitado ya no está disponible y no lo estará de nuevo. Debería ser utilizado cuando un recurso ha sido quitado de forma permanente.</p>
<p align="justify">Si un cliente recibe este código no debería volver a solicitar el recurso en el futuro. Por ejemplo un buscador lo eliminará de sus índices y lo hará más rápidamente que utilizando un código 404.</p>

**411 - Length Required**
<p align="justify">El servidor rechaza la petición del navegador porque no incluye la cabecera Content- Length adecuada.2</p>

**412 - Precondition Failed**
<p align="justify">El  servidor  no  es capaz de  cumplir  con  algunas  de  las  condiciones  impuestas por  el navegador en su petición.2</p>

**413 - Request Entity Too Large**
<p align="justify">La  petición  del  navegador  es  demasiado  grande  y  por  ese  motivo  el  servidor  no  la procesa2</p> 

**414 - Request-URI Too Long**
<p align="justify">La URI de la petición del navegador es demasiado grande y por ese motivo el servidor no la procesa (esta condición se produce en muy raras ocasiones y casi siempre porque el navegador envía como GET una petición que debería ser POST).2</p>

**415 - Unsupported Media Type**
<p align="justify">La petición del navegador tiene un formato que no entiende el servidor y por eso no se procesa.2</p>

**416 - Requested Range Not Satisfiable** 
<p align="justify">El  cliente  ha  preguntado  por  una  parte  de  un  archivo,  pero  el  servidor  no  puede proporcionar esa parte, por ejemplo, si el cliente preguntó por una parte de un archivo que está más allá de los límites del fin del archivo.</p>

**417 - Expectation Failed**
<p align="justify">La petición del navegador no se procesa porque el servidor no es capaz de cumplir con los requerimientos de la cabecera Expect de la petición.2</p>

**418 - I'm a teapot**
<p align="justify">Soy una tetera.</p>

**422 - Unprocessable Entity (WebDAV - RFC 4918)**
<p align="justify">La solicitud está bien formada pero fue imposible seguirla debido a errores semánticos.</p>
  
**423 - Locked (WebDAV - RFC 4918)**
<p align="justify">El recurso al que se está teniendo acceso está bloqueado.</p>

**424 - Failed Dependency (WebDAV) (RFC 4918)**
<p align="justify">La solicitud falló debido a una falla en la solicitud previa.</p>

**425 - Unassigned**
<p align="justify">Definido en los drafts de WebDav Advanced Collections, pero no está presente en "Web Distributed Authoring and Versioning (WebDAV) Ordered Collections Protocol" (RFC 3648).</p>
  
**426 - Upgrade Required (RFC 7231)** 
<p align="justify">El cliente debería cambiarse a TLS/1.0.</p>

**428 - Precondition Required**
<p align="justify">Ell servidor requiere que la petición del navegador sea condicional (este tipo de peticiones evitan los problemas producidos al modificar con PUT un recurso que ha sido modificado por otra parte).2 

**429 - Too Many Requests**
<p align="justify">Hay muchas conexiones desde esta dirección de internet.</p>

**431 Request Header Fileds Too Large)**
<p align="justify">El servidor no puede procesar la petición porque una de las cabeceras de la petición es demasiado grande. Este error también se produce cuando la suma del tamaño de todas las peticiones es demasiado grande.2</p>

**449** 
<p align="justify">Una  extensión  de  Microsoft:  La  petición  debería  ser  reintentada  después  de  hacer  la acción apropiada.</p> 

**451 - Unavailable for Legal Reasons**
<p align="justify">El  contenido  ha  sido eliminado  como  consecuencia  de  una orden  judicial o  sentencia emitida por un tribunal.</p> 

**5xx Errores de servidor** 

<p align="justify">El servidor falló al completar una solicitud aparentemente válida.</p>

<p align="justify">Los códigos de respuesta que comienzan con el dígito "5" indican casos en los cuales el servidor tiene registrado aún antes de servir la solicitud, que está errado o es incapaz de ejecutar la petición. Excepto cuando está respondiendo a un método HEAD, el servidor debe incluir  una  entidad  que  contenga  una  explicación  de  la  situación  de  error,  y  si  es  una condición temporal o permanente. Los agentes de usuario deben desplegar cualquier entidad incluida  al  usuario.  Estos  códigos  de  respuesta  son  aplicables  a  cualquier  método  de petición.</p>

**500 - Internal Server Error**
<p align="justify">Es  un  código  comúnmente  emitido  por  aplicaciones  empotradas  en  servidores  web, mismas que generan contenido dinámicamente, por ejemplo aplicaciones montadas en IIS o Tomcat, cuando se encuentran con situaciones de error ajenas a la naturaleza del servidor web.</p>

**501 - Not Implemented**
<p align="justify">El servidor no soporta alguna funcionalidad necesaria para responder a la solicitud del navegador (como por ejemplo el método utilizado para la petición).2</p>

**502 - Bad Gateway**
<p align="justify">El servidor está actuando de proxy o gateway y ha recibido una respuesta inválida del otro servidor, por lo que no puede responder adecuadamente a la petición del navegador.2</p>

**503 - Service Unavailable**
<p align="justify">El servidor no puede responder a la petición del navegador porque está congestionado o está realizando tareas de mantenimiento.2</p>

**504 - Gateway Timeout**
<p align="justify">El servidor está actuando de proxy o gateway y no ha recibido a tiempo una respuesta del otro servidor, por lo que no puede responder adecuadamente a la petición del navegador.2 505 - HTTP Version Not Supported</p>
<p align="justify">El servidor no soporta o no quiere soportar la versión del protocolo HTTP utilizada en la petición del navegador.2</p>

**506 - Variant Also Negotiates (RFC 2295)**
<p align="justify">El servidor ha detectado una referencia circular al procesar la parte de la negociación del contenido de la petición.2</p>

**507 - Insufficient Storage (WebDAV - RFC 4918)**
<p align="justify">El  servidor  no  puede  crear  o  modificar  el  recurso  solicitado  porque  no  hay  suficiente espacio de almacenamiento libre.2</p>

**508 - Loop Detected (WebDAV)**
<p align="justify">La petición no se puede procesar porque el servidor ha encontrado un bucle infinito al intentar procesarla.2</p>

**509 - Bandwidth Limit Exceeded**
<p align="justify">Límite de ancho de banda excedido. Este código de estatus, a pesar de ser utilizado por muchos servidores, no es oficial.</p>

**510 - Not Extended (RFC 2774)**
<p align="justify">La  petición  del  navegador  debe  añadir  más  extensiones  para  que  el  servidor  pueda procesarla.2</p>

**511 - Network Authentication Required**
<p align="justify">El navegador debe autenticarse para poder realizar peticiones (se utiliza por ejemplo con los portales cautivos que te obligan a autenticarte antes de empezar a navegar).2</p>

**Autor: Gustavo Adolfo Arellano Sandoval (arellano.gustavo@gmail.com)**
