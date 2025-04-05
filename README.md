# Sistema de monitoreo y gestión remota de invernaderos
Proyecto realizado dentro del marco del Trabajo Profesional de Ingeniería Eletrónica de la Facultad de Ingeniería de la Universidad de Buenos Aires

## Contenido 
Este repositorio contiene el docker compose de la plataforma utilizada para que los usuarios puedan interactuar con dispositivos del sistema. \

## Plataforma
- Plataforma IoT seleccionada: [OpenRemote](https://openremote.io/)

## Instalación del ambiente de desarrollo
- Requisitos: Docker Desktop
- Comandos: `docker-compose -p openremote up`

## Notas
- El docker compose en este repositorio fue obtenido de la página oficial de OpenRemote.
- Se modificó la versión de imagen del "Manager" a la versión 1.2.0 ya que dicha versión no presentaba problemas al momento de configurar el estilo de la UI.
- Se habilitó el puerto 1883 del container del "Manager" para interactuar con el Broker MQTT de OpenRemote
