# NodeMCU

Esta sección describe todo lo referido a la parte del proyecto que utiliza la placa NodeMCU.

## Introducción

[NodeMCU](https://en.wikipedia.org/wiki/NodeMCU) es una plataforma de código abierto y un kit de desarrollo que está basado en el chip ESP8266.
Es ideal para proyectos IoT por brindar conectividad inalámbrica WiFi.

Para construir el prototipo de casa inteligente, debe seguir los siguientes pasos.

### 1°) Conexiones

Lea el [archivo README](Conexiones/README.md) de la carpeta conexiones para saber sobre:

* la lista de materiales (sensores, etc) 
* el diagrama de conexiones eléctricas
* imagen ilustrativa de las conexiones en una placa de pruebas.

### 2°) Configuración del IDE Arduino

En la mayoría de los casos para poder trabajar con placas basadas en el chip ESP8266 se necesita una configuración adicional de nuestro IDE Arduino. Una breve explicación de la configuración del IDE Arduino para poder realizar nuestro proyecto se detalla [en este documento](Configuracion-IDE-Arduino/README.md).

### 3°) Código fuente Arduino - Sketch Arduino

[En esta parte](Sketchs-Arduino/) se encuentran los códigos fuentes utilizados. El mismo deberá ser cargado en la placa a través del IDE Arduino y del puerto serie de la placa.

### 4°) Conexión de la placa a la PC

Para que nuestra PC y el IDE Arduino detecten el puerto serie, al cual se conecta la placa, deberemos tener la precaución de conectar primero 
la placa a la PC con nuestro IDE Arduino cerrado. Una vez detectado el puerto abriremos nuestro IDE Arduino y lo seleccionaremos en tool -> Port  

![Port](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/NodeMCU-app/Port.png)


