# **Manual de la VUCEM 3.0**

Este documento cuenta con los diagramas de la VUCEM 3.0 con el objetivo de servir de referencia para analistas, desarrolladores, integradores de datos, administradores de bases de datos, infrestructura y todo el personal que necesite y requiera conocer los diagramas de la VUCEM

## 1. Diagrama general de vucem 2.5
![image](https://github.com/user-attachments/assets/aa3db512-9a09-4680-a878-cff071aad7b6)


## 2. Diagrama general de servicios rest
![image](https://github.com/user-attachments/assets/d2d116b8-2701-4855-a021-3cbee077b3c1)

## 3. Diagrama de secuencia de vucem 2.5
![image](https://github.com/user-attachments/assets/38369949-cfd3-4378-9195-2cdebcad876c)


### 3.1. Secuencia del flujo de una solicitud en vucem
![image](https://github.com/user-attachments/assets/496d08d8-b15f-48f4-9a19-3f59b034848f)

## 4. Vista de Procesos

### 4.1. Capa de presentación
En esta capa se ejecuta la transformación de la información procesada por la capa intermedia.

Básicamente tiene los siguientes componentes:

- Front controller: Encargado de obtener las peticiones ejecutadas por un cliente conocido (Web server) vía HTTP, o HTTP-Request, una vez obtenida la petición ejecuta un proceso de llamado al servicio correspondiente para atender la petición.
- Una vez atendida la petición, el Front controller hace uso de un ‘Layout manager’ para construir el contenido web o página que será despachado de regreso al cliente vía un componente JSP.
- Esta capa se comunica con todos los servicios de infraestructura para soportar los requerimientos no funcionales y utilerías comunes a la arquitectura.

1. Este es el diagrama de capas de presentacion
![image](https://github.com/user-attachments/assets/07a9bbc2-a5b2-4db7-a299-41c80ed34862)

2. En la figura siueinte se muestra la secuencia dinámica de interacción descrita
![image](https://github.com/user-attachments/assets/0584cb37-8566-4d73-9aec-2fdb56c439b4)

### 4.2. Capa de servicios
En esta capa se ejecuta el proceso lógico de negocio del aplicativo.

Básicamente tiene los siguientes componentes:

-Business service: Encargado de recibir la petición filtrada y traducida a objetos de negocio para ejecutar operaciones – lógica de negocio – sobre los datos recibidos.
- Business rule: Encargado de encapsular reglas de negocio claras y consistentes para especializar el manejo y cálculo de operaciones, facilitando encapsulamiento de conocimiento y favoreciendo la mantenibilidad.
- Business helper: Encargado de procesos auxiliares de procesamiento.
- Business domain: Encargado de representar entidades de negocio y sus atributos, sobre los cuales se ejecutan las operaciones del Business service de acuerdo a las Business rules.
- End point (Adapter): En caso de requerir exponer los servicios de negocio a otros clientes diferentes del cliente conocido –web- se utiliza un Adapter – End point dependiendo del protocolo particular de exposición de servicio (p.e. Web service). Cada componente tiene que ser tratado para su publicación ya que no hay publicación por default.

![image](https://github.com/user-attachments/assets/535c60c7-8ef7-40a3-bd25-b2eadc85ba76)

### 4.2.1. Diagrama de secuencia servicios
En la figura siguiente se muestra la secuencia dinámica de interacción descrita
![image](https://github.com/user-attachments/assets/b5c0bc02-f1ec-49a6-9c30-6d5cba92c0c3)

### 4.3. Capa de integración
En esta capa se ejecuta el proceso de integración a otros sistemas o a la persistencia misma de la propuesta arquitectónica.

Básicamente tiene los siguientes componentes:

1. Repository: Entidad encargada de especializar el tipo de comunicación – persistencia requerida dependiendo del back end.
2. Helper: Encargado ejecutar la transformación especifica (Query, invocación, empaquetado) especifico dependiendo del tipo de repositorio a utilizar.
3. Business domain: Encargado de representar entidades de negocio y sus atributos los cuales serán enviados al Repository pertinente.
4. Spring Channel: Encargado de la comunicación con Middleware de integración (MQ, Integrator, Interchange) a través de JMS para mensajería y FTP para generación y consumo de archivos.
5. Servicios de infraestructura: Contiene a los componentes y los subsistemas de soporte para los servicios funcionales (de negocio)

![image](https://github.com/user-attachments/assets/aae62298-bafc-42ee-b7eb-faa16b2c009f)

### 4.3.1. Diagrama de secuencia integracion
![image](https://github.com/user-attachments/assets/bff5bca5-3071-4bde-ab03-c41483b8db94)

### 4.4. Vista de implementación
La propuesta arquitectónica está organizada en 4 capas:
- De presentación.
- De servicios.
- De integración.
- De infraestructura.

Los elementos de una capa sólo pueden comunicarse con los elementos de la capa contigua:
1. Presentación –> Servicios
2. Servicios –> Integración
3. Presentación, Servicios o Integración -> Infraestructura

![image](https://github.com/user-attachments/assets/b3d96b4e-e885-4eea-a6a2-41185a748cb9)

### 4.4.1. Elementos de cada capa y sus relaciones
![image](https://github.com/user-attachments/assets/40acbf31-d62d-4e4f-b415-0e608959ab6b)

>Nota: Para mayor informacion de los tramites de la vucem visitar el sitio web del [SAT](https://www.sat.gob.mx/home)
