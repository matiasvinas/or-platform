# Sistema de monitoreo y gestión remota de invernaderos - Plataforma
Proyecto realizado dentro del marco del Trabajo Profesional de Ingeniería Eletrónica de la Facultad de Ingeniería de la Universidad de Buenos Aires


## Introducción al sistema de monitoreo y gestión
El sistema de monitoreo y gestión remota de invernadores consta de las siguientes partes:
- **Nodo sensor**: dispositivo responsable de medir temperatura, humedad del suelo, tensión de batería del sensor y envíar los datos a través de BLE Mesh al nodo gateway.
- **Nodo *gateway***: dispositivo responsable de controlar actuadores y envíar datos de los sensores a la plataforma web a través del protocolo MQTT.  
- **Plataforma web**: inplementada en AWS en base al proyecto de código abierto [Open Remote](https://openremote.io/), con la finalidad de controlar los nodos del sistema por parte del usuario.

Los nodos de la malla bluetooth están dispuestos como una red estrella donde el nodo gateway es el nodo central y el único que intercambia datos con la plataforma web.

![Diagrama del dispositivo Sensor](images/diagrama-solucion-propuesta.png)


## Enlaces útiles

[ Implementación de Open Remote en AWS ](/implementacion/README.md)

[ Configuración de la interfaz de la plataforma Open Remote ](/interfaz/README.md)

[ Firmware del nodo sensor](https://github.com/matiasvinas/esp32c3-sensor)

[Firmware del nodo *gateway*](https://github.com/matiasvinas/esp32c3-gateway)