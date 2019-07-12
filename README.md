# MatrIoTSASE2019

# Workshop Matr IoT para SASE 2019 - Simposio Argentino de Sistemas Embebidos 

## Instaladores

* Instala en tu celular [Mat|r Viewer]( https://play.google.com/store/apps/details?id=com.inosur.matr)
* Para testear MQTT sin necesidad de sensores usaremos [Mosquitto]( https://mosquitto.org/download/)
* Para programar sobre nodeMCU usamos el [Arduino IDE ](https://www.arduino.cc/en/Main/Software). Esta es la plataforma hardware sobre la cual trabajaremos en el taller


## Slides

[1- Introducción a Internet de las cosas - MQTT](https://docs.google.com/presentation/d/1XVnJ0plecw3oD37Usjq8RfObKmwj6wM1WdNtZ2kQkAY/edit?usp=sharing)

[2- Intro a Mat|r - Primera aplicación Mat|r con MQTT ](https://docs.google.com/presentation/d/1dJMVf1PW2CSBLgxwoCogAXe8xh_dOTfB2xqBnLhkxLo/edit?usp=sharing)

[3- Conectando tus sensores Arduino a Mat|r](https://docs.google.com/presentation/d/1Q4N4KBDeaxzQqAz7rKdHzow87QbtEnnqmYwSne3ce-8/edit?usp=sharing)

## Código fuente



## Test you Mat|r app with mosquitto - SASE2019-tutorial example

### Channel home

Canal de monitoreo *home*

Comando

```
mosquitto_pub -h a2sq3y7mdrjtom.iot.us-east-1.amazonaws.com -p 8883 -t a8cb7cc3 --cert arduinotest.certificate.pem  --key arduinotest.private-key.txt --cafile rootCA.pem -m '{"bulb1State":true,"temp":30,"hum":60}' -d

```

Salida esperada:

```
Client mosq/8dp2QyRi0ECSi7SBYF sending CONNECT
Client mosq/8dp2QyRi0ECSi7SBYF received CONNACK (0)
Client mosq/8dp2QyRi0ECSi7SBYF sending PUBLISH (d0, q0, r0, m1, 'a8cb7cc3', ... (38 bytes))
Client mosq/8dp2QyRi0ECSi7SBYF sending DISCONNECT
```
### Channel command

Canal de envío de comando para prender y apagar leds.

Comando

```bash
mosquitto_sub -h a2sq3y7mdrjtom.iot.us-east-1.amazonaws.com -p 8883 -t 3dff80bb --cert arduinotest.certificate.pem  --key arduinotest.private-key.txt --cafile rootCA.pem -d
```
Salida esperada 
```
Client mosq/cerdx5GO7JNgL06dFq sending CONNECT
Client mosq/cerdx5GO7JNgL06dFq received CONNACK (0)
Client mosq/cerdx5GO7JNgL06dFq sending SUBSCRIBE (Mid: 1, Topic: 3dff80bb, QoS: 0, Options: 0x00)
Client mosq/cerdx5GO7JNgL06dFq received SUBACK
Subscribed (mid: 1): 0
Client mosq/cerdx5GO7JNgL06dFq received PUBLISH (d0, q0, r0, m0, '3dff80bb', ... (39 bytes))
{"command":"TOGGLE-RELAY","relayIdx":1}
Client mosq/cerdx5GO7JNgL06dFq received PUBLISH (d0, q0, r0, m0, '3dff80bb', ... (39 bytes))
{"command":"TOGGLE-RELAY","relayIdx":1}
Client mosq/cerdx5GO7JNgL06dFq received PUBLISH (d0, q0, r0, m0, '3dff80bb', ... (39 bytes))
{"command":"TOGGLE-RELAY","relayIdx":1}
```

