# Implementación de Open Remote en AWS

El siguiente documento contiene las instrucciones para la implementación de una instancia personal de la plataforma Open Remote, a través de AWS marketplace, para el [ Sistema de monitoreo y gestión remota de invernaderos](/README.md), un proyecto realizado dentro del marco del Trabajo Profesional de Ingeniería Eletrónica de la Facultad de Ingeniería de la Universidad de Buenos Aires.

## Índice
- [Creación de cuenta en AWS](#creacion-de-cuenta-en-aws)
- [Compra de dominio en AWS](#compra-de-dominio-en-aws)
- [Implementación de Open Remote en AWS Markteplace](#implementacion-de-open-remote-en-aws-markteplace)
- [Configuración SSL del sitio](#configuracion-ssl-del-sitio)
- [Enlaces útiles](#enlaces-utiles)

## Creación de cuenta en AWS

1. Registro inicial
    1. Accede a la página oficial de creación de cuentas de AWS: [https://aws.amazon.com/es/resources/create-account/](https://aws.amazon.com/es/resources/create-account/)
    2. Haz click en **Crear una cuenta de AWS**.
    3. Introduce la dirección de correo electrónico del usuario raíz, asigna un nombre a tu cuenta y selecciona **Verificar dirección de correo electrónico**.  
  Recibirás un correo con un código de verificación que deberás ingresar para continuar.

2. Información de contacto
    1. Elige el tipo de cuenta/plan: **Personal** o **Empresa**.
    2. Completa los datos solicitados (nombre completo o razón social, dirección y teléfono).
    3. En cuentas empresariales, se recomienda usar el número fijo de la empresa en lugar de un móvil personal.

3. Método de pago
    1. Proporciona los datos de tu tarjeta de crédito o débito.
    2. Selecciona **Verificar** y luego **Agregar**.
    3. Puedes usar una dirección de facturación distinta seleccionando **Usar una nueva dirección** y repitiendo la verificación.

4. Verificación de identidad
    1. En la sección **Confirme su identidad**, selecciona recibir el código de verificación por **SMS** o **llamada**.
    2. Selecciona el país o código de región, ingresa tu número y escribe el código que recibas.
    3. Esta validación suele tardar unos minutos.

5. Activación final
    1. AWS procesará tu solicitud y, en breve, recibirás un correo de confirmación indicando que tu cuenta está activa y lista para usar.
    2. A partir de ese momento podrás iniciar sesión con el correo y la contraseña definidos durante el registro.

6. Recomendaciones
    - Activar la **autenticación multifactor (MFA)** en el usuario raíz para añadir una capa extra de protección.
    - No emplear el usuario raíz (root account) en el día a día.  
    - Crear usuarios **IAM** con los permisos mínimos necesarios y gestionar el acceso mediante políticas específicas.
    - Para mayor información y guía, visita:  

## Compra de dominio en AWS

1. Requisitos previos
    1. Tener una cuenta activa de AWS con permisos de administrador en **Route 53**.
    2. Disponer de un método de pago válido (tarjeta de crédito o débito).
    3. Conocer el nombre de dominio y la extensión (.com, .net, .org, etc.) que deseas adquirir.

2. Abre Amazon Route 53
    1. En la barra de búsqueda de la consola escribe “Route 53” y selecciona el servicio.
    2. Dentro de Route 53, haz clic en **Registrar dominio** (*Register domain*).

3. Busca y añade el dominio al carrito
    1. En el campo de texto escribe el nombre de dominio deseado junto con su extensión.
    2. Pulsa **Comprobar** para validar disponibilidad.
    3. Si está libre, selecciona **Agregar al carrito** (*Add to cart*).

4. Completa la información de registro
    1. Proporciona los datos de contacto del propietario (persona o empresa), incluyendo dirección postal y teléfono.
    2. Elige si deseas ocultar estos datos en el **WHOIS** (opción de privacidad).

5. Revisa y paga
    1. Verifica el resumen de la compra: nombre de dominio, extensión, periodo de registro y coste anual (entre 9 y varios cientos de USD según TLD).
    2. Confirma y liquida la factura inmediatamente para evitar cancelaciones automáticas pasados cinco días.
    3. AWS envía un mail con un link de confirmación al administrador para validar la compra del dominio. En caso de no confirmar, el dominio será eliminado.

## Implementación de Open Remote en AWS Markteplace

1. Para comprar y deployar **OpenRemote** en AWS Marketplace, se recomienda seguir las instrucciones del sitio oficial:
    - 🔗 [Guía oficial de OpenRemote](https://docs.openremote.io/docs/user-guide/deploying/aws-marketplace)

2. En *Route 53* agregar el subdominio `subdominio.mi-dominio.com` y configurarlo para que redireccione a la IP de la instancia EC2 donde se ejecuta la plataforma. 

## Configuración SSL del sitio

1. Acceso a la instancia EC2
    1. Accede desde la página de AWS a la instancia de EC2 y haz click en *Connect to Instance* con la configuración que se muestra en la siguiente imagen:
    
        ![EC2 Connection](/images/ec2-connect.png)

2. Creación del `.env`
    1. Crear un archivo `.env` en el mismo directorio donde se encuentra el archivo `dokcer-compose.yml`.
    2. Abre el `.env` y agrega la siguiente línea: `OR_HOSTNAME=subdominio.mi-dominio.com`
    3. Guarda los cambios y cierra el archivo.

        ![EC2 Console](/images/ec2-ssh.jpg)

3. Reinicio de containers
    1. Frenar el container donde se ejecuta el *manager* y volver a ejecturalo mediante los siguientes comandos:
        ```
        docker ps # lista los cointainers en ejecución
        docker stop <contenedor> # frena el container
        docker ps -a # indica el estado de los contenedores
        docker start <container> # vuelve a iniciar el container 
        ```

## Enlaces útiles

[Video de TravisMedia](https://www.youtube.com/watch?v=CjKhQoYeR4Q&t=105s&ab_channel=TravisMedia)



