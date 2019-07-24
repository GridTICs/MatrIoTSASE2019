#mosquitto
Este es un pequeño tutorial para el uso del protocolo MQTT mediante el software "mosquitto"

##Instalación en Windows
Para utilizar mosquitto sobre sistemas operativos Windows deberemos instalar programas adicionales.

###Instalación OpenSSL
OpenSSL es un software que nos ayudara a la hora de realizar comunicaciones encriptadas.
Para instalarlo debemos dirigirnos al siguiente [enlace](https://slproweb.com/products/Win32OpenSSL.html)

![OpenSSL](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/OpenSSL.png)

Y descargar e instalar según sea el caso

"Win32 OpenSSL 1.1.0* Light" o
"Win64 OpenSSL 1.1.0* Light"

Una vez descargado deberemos ejecutar el archivo ".exe"

![OpenSSL-exe](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/OpenSSL-exe.png)

Se abrirá un cuadro de dialogo y aceptaremos el acuerdo y presionaremos en "Next".

![OpenSSL-acuerdo](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/OpenSSL-acuerdo.png)

Elegimos la ubicación de la carpeta y presionamos en "Next".

![OpenSSL-File](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/OpenSSL-File.png)

Y destildamos la opción por defecto y realizamos click en "Install".

![OpenSSL-Free](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/OpenSSL-Free.png)

###Instalación Visual C++ para Visual Studio 2015

Deberemos ir a la siguiente [página] (https://www.microsoft.com/es-ar/download/details.aspx?id=48145)

![VisualC](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/VisualC.png)

Allí haremos click sobre el cuadro descargar.

Se nos presentaran dos opciones deberemos elegir la que corresponda con nuestro sistema operativo.

![VisualC-Archivo](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/VisualC-Archivo.png)

Luego damos cklick a ejecutar.

![VisualC-exe](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/VisualC-exe.png)

Aceptamos el acuerdo e instalamos.

![VisualC-Acuerdo](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/VisualC-Acuerdo.png)

###Instalación mosquitto

Ahora si nos dirigimos a la página de [eclipse mosquitto] (https://mosquitto.org/download/) y descargamos según la versión de nuestro sistema operativo.

![Mosquitto-download](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/Mosquitto-download.png)

Ejecutamos el archivo ".exe" descargado.

![Mosquitto-Setup](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/Mosquitto-Setup.png)

Seleccionamos la carpeta donde se instalaran los archivos del software.

![Mosquitto-Folder](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/Mosquitto-Folder.png)

Hacemos clik en "Next".

![Mosquitto-Service](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/Mosquitto-Service.png)

Nuevamente en "Next".

![Mosquitto-fin](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/Mosquitto-fin.png)

Y luego "Finish"

Ya tenemos instalado en windows mosquitto.

## Primeros Pasos

###Uso de MQTT mediante el puerto 1883.

Al utilizar el puerto 1883 no es necesario el uso de archivos certificados para realizar una comunicación con MQTT.
Para esta demostración además utilizaremos el servidor que nos provee la página de "eclipse mosquitto".
Primero abriremos la consola. Presionamos la tecla inicio de Windows y escribimos "cmd". Luego presionamos "Enter".

Ya en la consola deberemos dirigirnos a la carpeta donde se encuentra "mosquitto" instalado. Mediante los siguientes comandos.

```
C:\Windows\System32>cd ..
C:\Windows>cd ..
C:\>cd Program Files
C:\Program Files>cd mosquitto
```

Ahora ingresaremos el siguiente comando

```
C:\Program Files\mosquitto>mosquitto_sub -h test.mosquitto.org -t matr
```

Procederemos ahora a abrir otra consola y nos dirigiremos a la carpeta que contiene mosquitto. De la misma forma que en el anterior punto.

```
C:\Windows\System32>cd ..
C:\Windows>cd ..
C:\>cd Program Files
C:\Program Files>cd mosquitto
```

En esta nueva consola ingresaremos el siguiente comando.

```
C:\Program Files\mosquitto>mosquitto_sub -h test.mosquitto.org -t matr -m "Hola Mundo!!!" -d
```

###Uso de MQTT mediante el puerto seguro 8883.

Al usar la comunicación mediante el puerto 8883 deberemos usar un archivo certificado que nos provee el servidor.
En nuestro caso haremos un ejemplo con el servidor "test.mosquitto.org".
El archivo certificado lo podemos descargar desde el siguiente [enlace](https://test.mosquitto.org/).
En esa página descargaremos el archivo con [Formato PEM](https://test.mosquitto.org/ssl/mosquitto.org.crt).
Deberemos tener en cuenta donde se guarda el archivo para que después podamos acceder a el.

Ahora procederemos de igual forma que en los anteriores puntos.
Abrimos dos consolas y nos dirigiremos al lugar donde se encuentra instalado "mosquitto".
En una escribiremos el siguiente comando.

C:\Program Files\mosquitto>mosquitto_sub -h test.mosquitto.org -t matrIn -p 8883 --cafile d:\Users\juan\Desktop\mosquitto.org.crt

En la otra escribiremos este comando.

C:\Program Files\mosquitto>mosquitto_pub -h test.mosquitto.org -t matrIn -p 8883 --cafile d:\Users\juan\Desktop\mosquitto.org.crt -m "{\"command\":\"TOGGLE-RELAY\",\"relayIdx\":1}"

Como se puede observar especificamos el puerto con la sentencia "-p 8883" en el anterior paso este paso se omitía y "mosquitto" suponía una comunicación se realizaría sobre el puerto 1883.

Además mediante el comando "--cafile d:\Users\juan\Desktop\mosquitto.org.crt" le decimos a "mosquitto" donde se encuentra nuestro archivo certificado para la comunicación encriptada.
 
Para mayor información puede teclear el siguiente comando:
```
C:\Program Files\mosquitto>mosquitto --help
C:\Program Files\mosquitto>mosquitto_pub --help
C:\Program Files\mosquitto>mosquitto_sub --help
```
O visite la pagina de [eclipse mosquitto](https://mosquitto.org/) https://mosquitto.org/

