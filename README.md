# Detector-Sintomas-Covid
En este repositorio se encuentra todo lo necesario para armar un detector de sintomas covid.

## Descripción
Este programa ayuda a dar un protodiagnostico sobre los sintomas covid. El programa hace uso de el microcontrolador ESP32CAM, alguno de los sensores de la familia MAX30100 para obtener los datos de oxigeno en sangre y ritmo cardiaco del paciente, el sensor MLX90614 para obtener la tempratura del paciente, el protocolo MQTT para la transmición de datos y Node-Red para mostrar un display de toda la informacion y hacer un protodiagnostico.

## Material
Para que el código de este repositorio funcione, es necesario contar con lo siguiente:
 
- ESP32CAM
- IP Broker publico
- Programador FTDI con su cable
- Sensor MAX30100
- Sensor MLX90614
- Ubuntu 20.04
- IDE de Arduino 1.8 o superior
- Biblioteca PubSubClient para Arduino IDE
- Biblioteca WiFi para Arduino IDE
- Biblioiteca Adafruit_MLX90614.h
- Biblioteca MAX30105.h
- Broker Mosquitto funcionando de forma local en el puerto 1883
- NodeRed corriendo de forma local en el puerto 1880
- Nodos Dashboard para NodeRed

## Guías
Para configurar correctamente la IDE de Arduino para trabajar con el ESP32CAM, puedes consultar el siguiente enlace.

https://edu.codigoiot.com/course/view.php?id=850

Para configurar correctamente tu broker mosquitto puedes consultar el siguiente enlace.

https://edu.codigoiot.com/course/view.php?id=818

Para configurar correctamente NodeRed puedes consultar el siguiente enlace.

https://edu.codigoiot.com/course/view.php?id=817

Puedes obtener la biblioteca PubSubClient desde el siguiente enlace.

https://github.com/knolleary/pubsubclient

El microcontrolador publica en el tema `codigoIoT/detectorSintomas/flow` y lee en el tema `codigoIoT/detectorSintomas/esp`

## Funcionamiento
Para observar el funcionamiento de este proyecto deberás realizar lo siguiente.

#### ESP32 CAM
1. Modificar el archivo ESP32CAM_MQTT_MAX30100_MLX90614_JSON.ino con los el SSID, contraseña de tu red WiFi y con la IP de tu localhost.
2. Conecta los sensores a los pines del ESP32CAM como se indica en la sección "Guia de conexión de sensores" en el encabezado del archivo ESP32CAM_MQTT_MAX30100_MLX90614_JSON.ino.
3. Carga el programa ESP32CAM_MQTT_MAX30100_MLX90614_JSON.ino en el ESP32CAM.
4. Conectar el microcontrolador a la corriente eléctrica.
5. En caso de ser nesesario cambiar los temas de lectura y publicación del protocolo mqtt.

#### Node-Red
1. Carga el flow Detector_Sintomas_COVID.json que se encuentra en la carpeta Node-Red en NodeRed.
2. Modificar la IP que utilizaras para el localhost.
3. Si cambio los te mas de publicación y lectura de mqtt en el archivo .ino tambien debe cambiar el tema en el nodo MQTT in.
4. Visita el dashboard de NodeRed

#### MySQL
1. Seguir las instrucciones del archivo instrucciones.md dentro de la carpeta MySQL

![](https://github.com/EduCabreraMendoza/Detector-Sintomas-Covid/blob/main/dahsboard.PNG)



Creado el 5-sep-2022 por [Eduardo Cabrera](https://github.com/EduCabreraMendoza)