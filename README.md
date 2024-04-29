# Sistema de Monitoreo y Control de Distancia

Este proyecto implementa un sistema de monitoreo y control de distancia utilizando un dispositivo IoT conectado a una red Wi-Fi y a un broker MQTT. El dispositivo mide la distancia utilizando un sensor ultrasónico y controla dos LEDs en base a la distancia medida. Además, puede ser activado o desactivado mediante mensajes MQTT.

## Requisitos

- Placa de desarrollo compatible con Arduino
- Sensor ultrasónico HC-SR04
- LEDs (preferiblemente de colores amarillo y rojo)
- Conexión a una red Wi-Fi
- Acceso a un broker MQTT

## Librerías Utilizadas

- WiFi.h: para la conexión a la red Wi-Fi.
- PubSubClient.h: para la comunicación MQTT.

## Configuración

Antes de cargar el código en la placa de desarrollo, asegúrate de modificar las siguientes constantes según tu configuración:

- `WIFI_SSID`: SSID de tu red Wi-Fi.
- `WIFI_PASS`: Contraseña de tu red Wi-Fi.
- `MQTT_BROKER_HOST`: Dirección del servidor MQTT.
- `MQTT_BROKER_PORT`: Puerto del servidor MQTT.
- `MQTT_CLIENT_ID`: Identificador único del cliente MQTT.
- `PUBLISH_TOPIC`: Tema al cual se publicarán las lecturas de distancia.
- `SUBSCRIBE_TOPIC`: Tema al cual el dispositivo estará suscrito para recibir mensajes de control.

## Funcionamiento

1. El dispositivo se conecta a la red Wi-Fi y al servidor MQTT al ser encendido.
2. Mide la distancia utilizando el sensor ultrasónico y controla los LEDs en base a la distancia medida.
3. Publica la distancia medida en el tema especificado.
4. Escucha mensajes MQTT en el tema de suscripción. Si recibe el mensaje "LED_ON", activa el sistema; si recibe "LED_OFF", lo desactiva.

## Pinout

- `TRIGGER_PIN`: Pin de salida para enviar el pulso al sensor ultrasónico.
- `ECHO_PIN`: Pin de entrada para recibir el eco del pulso del sensor ultrasónico.
- `LED_AMARILLO`: Pin para controlar el LED amarillo.
- `LED_ROJO`: Pin para controlar el LED rojo.

## Notas

- Asegúrate de tener correctamente configurados el nombre de la red Wi-Fi y la contraseña, así como la dirección del broker MQTT.
- El intervalo de publicación de lecturas de distancia se encuentra configurado en 2 segundos. Puedes ajustarlo según tus necesidades en la función `checkAndControlSystem()`.
- El umbral de distancia para activar el LED amarillo se encuentra en 15 cm y para activar el LED rojo es entre 15 y 100 cm. Puedes ajustar estos valores en la función `controlLEDs()`.

---

Este README proporciona una visión general del proyecto, su configuración y su funcionamiento básico. Puedes expandirlo añadiendo más detalles según sea necesario.
