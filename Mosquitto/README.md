#mosquitto
Este es un peque�o tutorial para el uso del protocolo MQTT mediante el software "mosquitto"

##Instalaci�n en Windows
Para utilizar mosquitto sobre sistemas operativos Windows deberemos instalar programas adicionales.

###Instalaci�n OpenSSL
OpenSSL es un software que nos ayudara a la hora de realizar comunicaciones encriptadas.
Para instalarlo debemos dirigirnos al siguiente [enlace](https://slproweb.com/products/Win32OpenSSL.html)

![OpenSSL](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/OpenSSL.png)

Y descargar e instalar seg�n sea el caso

"Win32 OpenSSL 1.1.0* Light" o
"Win64 OpenSSL 1.1.0* Light"

Una vez descargado deberemos ejecutar el archivo ".exe"

![OpenSSL-exe](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/OpenSSL-exe.png)

Se abrir� un cuadro de dialogo y aceptaremos el acuerdo y presionaremos en "Next".

![OpenSSL-acuerdo](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/OpenSSL-acuerdo.png)

Elegimos la ubicaci�n de la carpeta y presionamos en "Next".

![OpenSSL-File](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/OpenSSL-File.png)

Y destildamos la opci�n por defecto y realizamos click en "Install".

![OpenSSL-Free](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/OpenSSL-Free.png)

###Instalaci�n Visual C++ para Visual Studio 2015

Deberemos ir a la siguiente [p�gina] (https://www.microsoft.com/es-ar/download/details.aspx?id=48145)

![VisualC](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/VisualC.png)

All� haremos click sobre el cuadro descargar.

Se nos presentaran dos opciones deberemos elegir la que corresponda con nuestro sistema operativo.

![VisualC-Archivo](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/VisualC-Archivo.png)

Luego damos cklick a ejecutar.

![VisualC-exe](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/VisualC-exe.png)

Aceptamos el acuerdo e instalamos.

![VisualC-Acuerdo](https://github.com/GridTICs/MatrIoTSASE2019/blob/master/Mosquitto/VisualC-Acuerdo.png)

###Instalaci�n mosquitto

Ahora si nos dirigimos a la p�gina de [eclipse mosquitto] (https://mosquitto.org/download/) y descargamos seg�n la versi�n de nuestro sistema operativo.

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

Al utilizar el puerto 1883 no es necesario el uso de archivos certificados para realizar una comunicaci�n con MQTT.
Para esta demostraci�n adem�s utilizaremos el servidor que nos provee la p�gina de "eclipse mosquitto".
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

Al usar la comunicaci�n mediante el puerto 8883 deberemos usar un archivo certificado que nos provee el servidor.
En nuestro caso haremos un ejemplo con el servidor "test.mosquitto.org".
El archivo certificado lo podemos descargar desde el siguiente [enlace](https://test.mosquitto.org/).
En esa p�gina descargaremos el archivo con [Formato PEM](https://test.mosquitto.org/ssl/mosquitto.org.crt).
Deberemos tener en cuenta donde se guarda el archivo para que despu�s podamos acceder a el.

Ahora procederemos de igual forma que en los anteriores puntos.
Abrimos dos consolas y nos dirigiremos al lugar donde se encuentra instalado "mosquitto".
En una escribiremos el siguiente comando.

C:\Program Files\mosquitto>mosquitto_sub -h test.mosquitto.org -t matrIn -p 8883 --cafile d:\Users\juan\Desktop\mosquitto.org.crt

En la otra escribiremos este comando.

C:\Program Files\mosquitto>mosquitto_pub -h test.mosquitto.org -t matrIn -p 8883 --cafile d:\Users\juan\Desktop\mosquitto.org.crt -m "{\"command\":\"TOGGLE-RELAY\",\"relayIdx\":1}"

Como se puede observar especificamos el puerto con la sentencia "-p 8883" en el anterior paso este paso se omit�a y "mosquitto" supon�a una comunicaci�n se realizar�a sobre el puerto 1883.

Adem�s mediante el comando "--cafile d:\Users\juan\Desktop\mosquitto.org.crt" le decimos a "mosquitto" donde se encuentra nuestro archivo certificado para la comunicaci�n encriptada.
 
Para mayor informaci�n puede teclear el siguiente comando:
```
C:\Program Files\mosquitto>mosquitto --help
C:\Program Files\mosquitto>mosquitto_pub --help
C:\Program Files\mosquitto>mosquitto_sub --help
```
O visite la pagina de [eclipse mosquitto](https://mosquitto.org/) https://mosquitto.org/

