**1. Convenciones de Nombrado Para bases de datos**

**1.1 Nombre de objetos y conjuntos de datos** 

<p align="justify"> Esta  sección  discute  las  convenciones  de  nombrado  estándar  para  objetos  y  conjuntos  de  datos.  Estas convenciones fueron diseñadas para satisfacer los siguientes objetivos: </p>

- <p align="justify">Garantizar unicidad en los nombre de los objetos contenidos en una base de datos.</p>
- <p align="justify">Proveer una estructura de nombrado uniforme para los objetos de tipo similar.</p>
- <p align="justify">Simplificar las decisiones el diseño físico de la base de datos sin tomar en cuenta las estrategias de nombrado.</p>
- <p align="justify">Proveer la capacidad de visualizar un grupo de objetos por su aplicación y/o área en la cual los objetos fueron diseñados para brindar soporte.</p>

**1.1.1. Uso** 

<p align="justify"> Los siguientes estándares de nombrado aplican a cualquier objeto (base de datos, espacio de tablas, tablas, vistas, rutinas PL/SQL, etc.) utilizadas para sostener o mantener los datos del usuario, así como para los objetos externos del usuario (archivos, directorios, nombre de scripts, etc.) que serán utilizados en conjunción como parte de una aplicación de desarrollo estandarizado y procedimientos de operación del sistema. </p>

**1.1.2. Formato de nombrado estándar** 

<p align="justify"> Todos los objetos serán nombrados de acuerdo a los formatos de estándares listados en la siguiente tabla. Adicionalmente, se deberán seguir las siguientes reglas: </p>

- <p align="justify"> Todos los nombres de los objetos deben comenzar con un carácter alfabético.</p>
- <p align="justify"> Todos los nombres de los objetos deben estar en minúsculas.</p> 
- <p align="justify"> Todos los nombres de las tablas y de las vistas deberán estar en singular.</p>
- <p align="justify"> Es obligatorio el uso de guiones bajos para separar palabras que forman el nombre de una tabla o columna.</p>
- <p align="justify"> Está  permitido  el  uso  de  prefijos  u  sufijos  si  es  que  estos  son  estrictamente  necesarios  y  se justifican plenamente. Por ejemplo, las vistas pueden ser prefijadas con “vw\_”.</p>
- <p align="justify"> En  las  sentencias  DML  (data  manipulation  language)  las  palabras  reservadas  serán  escritas  en mayúsculas. (ej. SELECT id, nombre FROM prsona WHERE id=1).</p>
- <p align="justify"> No  están  permitidos  caracteres  especiales.  Se  recomienda  el  uso  únicamente  de:  [a-z] [0-9] y [\_] ()es decir, minúsculas, números y guiones bajos.</p>
- <p align="justify"> En la medida de lo posible, evitar abreviaciones.</p>



|**Tipo de Objeto** |**Atributos del nombre requeridos** |**Ejemplo** |
| - | - | - |
|Instancia|<p align="justify">-Nombre de más de 8 caracteres;</p><p align="justify">-Empezar con el identificador de la aplicación;</p><p align="justify">-Finalizar con d si es una base de desarrollo, t si  es  una  base  de  datos  de  validación /pruebas,  p  si  es  una  base  de  datos  de producción </p><p align="justify">-Debe ser único en el ambiente del servidor.</p> |<p>echimpd</p> <p>echimpt</p> <p>echimpp</p>|
|Base de datos|<p align="justify">-Mismo nombre que el nombre de la instancia seguido de las convenciones de nombrado de instancia</p><p align="justify">-Debe ser único dentro de la instancia.</p>|<p>echimpd</p> <p>echimpt</p> <p>echimpp</p>|
|Espacio de tabla|<p align="justify">-Nombre de más de 25 caracteres;</p><p align="justify">-Comenzar con el identificador de la aplicación y terminar con;</p><p align="justify">**-\_data** si el espacio de tabla sujeta datos;</p><p align="justify">**-\_indx**  si  el  espacio  de  tabla  sujeta  datos indexados;</p><p align="justify">-Debe ser único en la base de datos.</p>|<p align="justify">adm\_data,</p><p align="justify">adm\_indx</p>|
|Tabla|<p align="justify">-Nombre de (máximo) 30 caracteres</p><p align="justify">-Nombre en singular</p><p align="justify">-No debe contener palabras reservadas o caracteres especiales.</p>|<p align="justify">factura,</p><p align="justify">persona,</p><p align="justify"> viaje_redondo</p> |
|Índice|<p align="justify">-Máximo 30 caracteres;</p><p align="justify">-Debe ser único dentro de la base de datos; Debe iniciar con idx_</p><p align="justify">-Debe tener el nombre de la tabla, con el sufijo del tipo de índice.</p>|<p align="justify">idx\_correo</p>|
|Vista|<p align="justify">-Misma normativa que una tabla Puede llevar un prefijo vw_</p>|<p align="justify">vw_informacion</p> |
|Columna|<p>￿ ￿ </p><p>￿ ￿ </p><p>￿ ￿ </p><p>￿ </p>|<p>Máximo 30 caracteres; </p><p>Evitar abreviaciones, aunque son permisibles en caso de descriptores muy largos </p><p>Debe  ser  único  dentro  de  la  tabla  o  vista correspondiente; </p><p>Debe derivar del nombre del identificador de negocio  durante  el  proceso  de  análisis  de negocio/datos; </p><p>El nombre de la columna no debe contener palabras reservadas o caracteres especiales. Si  la  entidad  posee  una  columna  numérica que coincide con su llave primaria, éste será nombrada “id”. </p><p>Todas  las  palabras  abreviadas  deben  ser obtenidas de una lista de abreviaciones CMS estandarizado,  para  más  información  vea “Creating Physical Names” en los estándares de administración de datos;</p>|provider, ap\_patrno, fecha\_alta, id|
|Restricción  de columna|￿ |Las  restricciones  de  la  columna  deben  estar construidas  por  el  identificador  de  la aplicación,  seguido  del  nombre  de  la columna, con el prefijo **ck\_**.|ck\_adm\_provider \_id|
|Llave Primaria|<p>￿ ￿ </p><p>￿ </p>|<p>Nombre de (máximo) 30 caracteres; </p><p>El  nombre  de  la  llave  primaria  debe  ser  el nombre de la tabla con el postfijo \_**pk** </p><p>El nombre de la llave primaria debe ser único dentro  de  la  definición  de  la  tabla correspondiente.</p>|provider\_pk|
|Llave foránea|￿ ￿ |<p>Nombre de (máximo) 30 caracteres; </p><p>El  nombre  de  la  llave  foránea  debe  ser  el nombre de la tabla con el postfijo **\_fk**; </p>|provider\_fk|
||￿ |El nombre de la llave foránea debe ser única dentro  de  la  definición  de  la  tabla correspondiente.||
| :- | - | - | :- |
|Procedimiento, función, paquete|<p>￿ ￿ </p><p>￿ </p>|<p>Nombre de (máximo) 30 caracteres; </p><p>Prefijo  con  el  identificador  de  la  aplicación, seguido de su descripción; </p><p>Sufijo  del  **\_proc**  (procedimiento),  **\_func** (función), o **\_pkg** (paquete).</p>|hcis\_get\_cust\_id\_ proc hcis\_get\_cust\_id\_ func hcis\_get\_cust\_id\_ pkg|
|Esquema|￿ |Usualmente el identificador de la aplicación|Hcis|
|Campo  que  hace referencia  a  una llave  “unaria”  en otra tabla. |￿ |Deberá iniciar co el prefijo “id\_” seguido del nombre  de  la  tabla  al  que  hace  referencia. Esto es común con los campos que son llaves foráneas. |id\_usuario id\_estado |

**Notas** 

1) Cualquier cambio a la presente debe ser propuesto, justificado y aprobado para su incorporación antes de ser implementado en cualquier desarrollo 
1) Los criterios no cubiertos en la presente deberán ser expuestos para posteriormente ser evaluados y aceptados (o rechazados) según sea el caso 

**Última actualización: 5 de Octubre de 2021 (12:52)** 
