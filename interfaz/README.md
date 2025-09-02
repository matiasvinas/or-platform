# Configuración de la interfaz de la plataforma Open Remote

El siguiente documento contiene las instrucciones de configuración de la interfaz de la plataforma Open Remote para el [ Sistema de monitoreo y gestión remota de invernaderos](/README.md)
, un proyecto realizado dentro del marco del Trabajo Profesional de Ingeniería Electrónica de la Facultad de Ingeniería de la Universidad de Buenos Aires.

## Índice
- [Creación del *asset* nodo *gateway*](#creacion-del-asset-nodo-gateway)
- [Creación del *asset* nodo sensor](#creacion-del-asset-nodo-sensor)
- [Creación del tablero](#creacion-del-tablero)
- [Creación de alarma](#creacion-de-alarma)

## Creación del *asset* nodo *gateway*

1. Ingresa a la plataforma Open Remote y luego a la sección 'Assets'.
2. Agrega un nuevo *asset* y selecciona *Thing Asset*
3. Ingresa el nombre: "Nodo *Gateway*".
5. Ingresa al *asset* creado y selecciona *Modify*.
4. Agrega los siguientes atributos al *asset* creado:

    |Variable|Name|Type|Configuration items|
    |----|----|-------|------|
    |Frecuencia |frecuencia|Number|Label: "frecuencia de muestreo" <br> Units: ["seconds"] <br> Acees public read: true|
    |Riego|riego_activado|Boolean|Label: "Sistema de riego activado" <br> Acees public read: true|
    |Nodo sensor 1 |nodo_sensor_1_conectado|Boolean|Label: "Nodo sensor 1 conectado" <br> Rule state: true |
    |Nodo sensor 2 |nodo_sensor_2_conectado|Boolean|Label: "Nodo sensor 2 conectado" <br> Rule state: true |
    |Nodo sensor 3 |nodo_sensor_3_conectado|Boolean|Label: "Nodo sensor 3 conectado" <br> Rule state: true |

## Creación del *asset* nodo sensor

1. Ingresa a la plataforma Open Remote y luego a la sección 'Assets'.
2. Agrega un nuevo *asset* y selecciona *Thing Asset*.
3. Ingresa el nombre: "Nodo Sensor 1".
4. En *parent node*, seleeciona "Nodo *gateway*.
5. Agrega los siguientes atributos al *asset* creado:

    |Variable|Name|Type|Configuration items|
    |----|----|-------|------|
    |Batería |bateria|Number|Label: "bateria" <br> Units: ["volts"] <br> Format: {"minimumFractionDigits":2,"maximumFractionDigits":2} <br> Acees public read: true|
    |Humedad del suelo|humedad|Number|Label: "Humedad del suelo" <br> Units: ["percentage"] <br> Format: {"minimumFractionDigits":2,"maximumFractionDigits":2} <br> Store data points: true <br> Read only: true |
    |Temperatura |temperatura|Number|Label: "Temperatura" <br> Units: ["celsius"] <br> Format: {"minimumFractionDigits":2,"maximumFractionDigits":2} <br> Store data points: true <br> Read only: true |

6. Repite los pasos anteriores para crear los *assets*:
    - "Nodo Sensor 2"
    - "Nodo Sensor 3"


## Creación del tablero
1. Ingresa a la plataforma Open Remote y luego a la sección 'Insights'.
2. Crea un nuevo *dashboard* y dentro de este, selecciona *Modify*.
3. Para el atributo "Frecuencia de muestreo", agrega un *widget attribute* con la siguiente configuración:

    |Configuración|Valor|
    |----|----|
    |Allow user input | true |
    |Show time of last update | true |

4. Para el atributo "Sistema de riego activado", agrega un *widget attribute* con la siguiente configuración:

    |Configuración|Valor|
    |----|----|
    |Allow user input | true |
    |Show time of last update | true |

5. Para todos los atributos "Nodo sensor conectado", agrega un *widget attribute* con la siguiente configuración:

    |Configuración|Valor|
    |----|----|
    |Allow user input | false |
    |Show time of last update | true |

6. Para todos los atributos "Batería", agrega un *widget gauge* con la siguiente configuración:

    |Configuración|Valor|
    |----|----|
    |minimum value | 6 |
    |maximum value | 9 |
    |Threhold red color | 6 |
    |Threhold orange color | 6,6 |
    |Threhold green color | 9 |

7. Para todos los atributos "Humedad del suelo", agrega un *widget gauge* con la siguiente configuración:

    |Configuración|Valor|
    |----|----|
    |minimum value | 0 |
    |maximum value | 100 |
    |Threhold red color | 0 |
    |Threhold orange color | 20 |
    |Threhold green color | 40 |

8. Para todos los atributos "Humedad del suelo", agrega un *widget line chart* con la siguiente configuración:

    |Configuración|Valor|
    |----|----|
    |Default timeframe | Last Hour |
    |Allow time range selection | true |
    |Show legend | true |
    |Y-axis max | 30 |
    |X-axis min | 0 |

## Creación de alarma

1. Ingresa a la plataforma Open Remote y luego a la sección 'Rules'.
2. Agrega una nueva regla *When-Then*.
3. Selecciona *Always Active*.
4. En el cuadrante *When*, agrega la siguiente configuración:

    |Configuración|Valor|
    |----|----|
    |Asset | Nodo Gateway |
    |Attribute | Nodo sensor 1 conectado |
    |Operator | false |

5. En el cuadrante *Then*, configura el parámetro *Severity* como *Medium*.
6. Guarda configuración.
7. Para observar las alarmas, clickea en el ícono de la campana ubicado en la parte superior.
